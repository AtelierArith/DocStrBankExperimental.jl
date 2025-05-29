```
IntegDomain(
    fes::S,
    integration_rule::IR,
    axisymmetric::Bool,
    otherdimension::T,
) where {S<:AbstractFESet, IR<:AbstractIntegRule, T<:Number}
```

軸対称モデル用に構築します。他の次元は数値として与えられます。
