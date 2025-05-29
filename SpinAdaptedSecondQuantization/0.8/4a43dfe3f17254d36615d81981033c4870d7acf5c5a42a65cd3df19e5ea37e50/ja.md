```
set_color(S, [color=default_color(S)])
```

指定された色、または指定がない場合はデフォルトの色に、与えられた軌道空間の色を設定します。許可されている色は、[Base.text_colors](https://github.com/JuliaLang/julia/blob/17cfb8e65ead377bf1b4598d8a9869144142c84e/base/util.jl#L5-L34) 辞書によって示されています。これには、対応する色がこの[Wikipedia](https://en.wikipedia.org/wiki/ANSI_escape_code#8-bit)の表にある0-255の範囲の整数が含まれます。
