```
PGF([output::Union{IO,AbstractString}], width=√200cm, height=10cm, only_tikz=false; texfonts=false) -> Backend
```

Create a Portable Graphics Format backend.  The output is normally passed to [`draw`](@ref).   Specify a filename using a string as the first argument.  If `only_tikz` is true then the output is a "tikzpicture", otherwise the output is a complete latex document with headers and footers.  If `texfonts` is false, include "\usepackage{fontspec}" in the headers.

# Examples

```
c = compose(context(), rectangle())
draw(PGF("myplot.tex", 10cm, 5cm, true, texfonts=true), c)
```
