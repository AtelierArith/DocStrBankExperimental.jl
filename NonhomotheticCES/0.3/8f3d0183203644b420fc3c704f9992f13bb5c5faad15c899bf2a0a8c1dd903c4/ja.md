```julia
log_sectoral_consumptions(U, p̂, Ê, Ĉ)

```

**ログ** セクター消費を計算し、ベクトルとして返します。引数はログであり、`Ĉ` を取得するためにも使用されるべき [`log_consumption_aggregator`](@ref) を参照してください。

予算制約が成り立ちます。すなわち、

```julia
logsumexp(log_sectoral_consumptions(U, p̂s, Ê, Ĉ) .+ p̂s) ≈ Ê
```
