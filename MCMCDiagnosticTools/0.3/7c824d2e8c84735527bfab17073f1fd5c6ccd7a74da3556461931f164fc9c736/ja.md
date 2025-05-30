```
ess_rhat(
    samples::AbstractArray{<:Union{Missing,Real}};
    kind::Symbol=:rank,
    kwargs...,
) -> NamedTuple{(:ess, :rhat)}
```

サンプルの有効サンプルサイズと $\widehat{R}$ を推定します。`samples` の形状は `(draws, [chains[, parameters...]])` です。

ESS と $\widehat{R}$ の両方が必要な場合、このメソッドは `ess` と `rhat` を別々に呼び出すよりも効率的であることが多いです。

サポートされている `kind` の説明については [`rhat`](@ref) を、`kwargs` の説明については [`ess`](@ref) を参照してください。
