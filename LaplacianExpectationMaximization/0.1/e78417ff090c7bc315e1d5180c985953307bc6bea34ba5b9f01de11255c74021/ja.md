```julia
BIC_int(data, model, params; kw...)

```

母集団からサンプリングすることによってベイズ情報基準を推定します。キーワード引数 `kw` は [`mc_marginal_logp`](@ref) に渡されます。
