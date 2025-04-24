# ftlfmt

I've been working with some egregious `.ftl` files recently and [nvim](https://github.com/neovim/neovim)s XML formatter just can't seem to get them right.
This tool is a bare minimum implementation that is supposed to format [freemarker](https://github.com/apache/freemarker) files. `ftlfmt` will not break the structure of the given file, it will only indent.

## Usage
```
ftlfmt -h
Format freemarker files.
Version: 1.0.0

usage: ftlfmt [options] <string>

 -f, --file     pass a file to format.
 -o, --output   write output to a file.
 -s, --spaces   number of spaces to indent with.
                default: 4
 -t, --tabs     number of tabs to indent with.
                default: 1
```

### Basic Usage
To format a given string you can pass it directly.
```bash
ftlfmt "<root>
<foo>
<bar/>
</foo>
</root>"
```
Output:
```xml
<root>
	<foo>
		<bar/>
	</foo>
</root>
```

Also possible:
```bash
cat file.ftl | ftlfmt
ftlfmt -f file.ftl
```

### Indentation

`ftlfmt` is supposed to be as simple a tool as possible. By default it will use tabs to indent lines, but you can also use spaces.
```bash
# will use four spaces by default
ftlfmt -f file.ftl -s
# indent using two speaces
ftlfmt -f file.ftl -s2
```

To get some control of tab indentation you may also use this.
```bash
# using two tabs per indent
ftlfmt -f file.ftl -t2
```
