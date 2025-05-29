```
IntegDomain(
    fes::S,
    integration_rule::IR,
    axisymmetric::Bool,
) where {S<:AbstractFESet, IR<:AbstractIntegRule}
```

軸対称モデルのために、デフォルトの方向行列（単位行列）で構築します。もう一つの次元はデフォルトの単位（1.0）です。

これはおそらく `axisymmetric = true` のときに呼び出されるでしょう。デフォルトは `axisymmetric = false` です。
