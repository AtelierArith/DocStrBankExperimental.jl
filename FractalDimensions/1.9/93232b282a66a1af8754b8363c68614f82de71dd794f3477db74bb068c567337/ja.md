```
boxassisted_correlation_dim(X::AbstractStateSpaceSet; kwargs...)
```

[BuenoOrovio2007](@cite) のボックス支援最適化を使用して、`X` の相関次元 `Δ_C` を推定します。

この関数は非常に単純なことを行います：

```julia
εs, Cs = boxed_correlationsum(X; kwargs...)
slopefit(log2.(εs), log2.(Cs))[1]
```

したがって、詳細情報と利用可能なキーワードについては [`boxed_correlationsum`](@ref) を参照してください。
