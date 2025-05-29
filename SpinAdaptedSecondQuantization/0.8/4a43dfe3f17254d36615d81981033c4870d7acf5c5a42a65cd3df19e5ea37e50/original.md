```
set_color(S, [color=default_color(S)])
```

Sets the color of a given orbital space to the specified color, or the default if none is given. Allowed colors are given by the [Base.text_colors](https://github.com/JuliaLang/julia/blob/17cfb8e65ead377bf1b4598d8a9869144142c84e/base/util.jl#L5-L34) dict. This includes integers in the range 0-255 which the corresponding colors can be found in this table on [Wikipedia](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit).
