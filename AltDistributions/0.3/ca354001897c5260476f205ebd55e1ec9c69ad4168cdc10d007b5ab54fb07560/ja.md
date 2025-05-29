```julia
StdCorrFactor(σ, F)

```

共分散行列 `Σ = LL'` の因子 `L` は `L = Diagonal(σ) * F` として与えられます。乗算を行うことなく、`L` の代わりに使用できます。
