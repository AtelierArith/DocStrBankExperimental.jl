```
jackknife_full(g::Function, a[, b, ...])
```

与えられた関数 `g(<a>, <b>, ...)` がサンプル `a`、`b` などの平均に作用する場合のジャックナイフ推定、バイアス、および誤差を返します。

例:     # サンプル xs が与えられていると仮定     # サンプル xs の分散     g(x2, x) = x2 - x^2     estimate, bias, error = jackknife_full(g, xs.^2, xs)

関連: [`estimate`](@ref), [`bias`](@ref), [`std_error`](@ref)
