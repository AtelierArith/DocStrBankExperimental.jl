```
jackknife(g::Function, a[, b, ...])
```

与えられた関数 `g(<a>, <b>, ...)` がサンプル `a`、`b` などの平均に作用する場合のジャックナイフ推定値と誤差を返します。

例:     # サンプル xs が与えられていると仮定     # サンプル xs の分散     g(x2, x) = x2 - x^2     error = jackknife(g, xs.^2, xs)

関連: [`estimate`](@ref), [`std_error`](@ref)
