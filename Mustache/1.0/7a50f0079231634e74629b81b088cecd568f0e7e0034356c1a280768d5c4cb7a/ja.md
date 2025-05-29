```
jmt"string"
```

ドル記号でエスケープされた値を補間し、その後文字列を解析する文字列マクロです。

注: [HypertextLiteral](https://github.com/clarkevans/HypertextLiteral.jl/blob/master/src/macros.jl) のマクロを修正したものです。

例:

```
x = 1
toks = jmt"$(2x) by {{:a}}"
toks(; a=2) # "2 by 2"
```
