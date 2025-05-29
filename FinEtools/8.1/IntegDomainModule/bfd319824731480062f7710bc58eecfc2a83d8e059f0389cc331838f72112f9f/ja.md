```
IntegDomain(
    fes::S,
    integration_rule::IR,
    otherdimension::F,
) where {S<:AbstractFESet, IR<:AbstractIntegRule, F<:Function}
```

デフォルトの方向行列（単位行列）を使用して構築し、他の次元は関数によって提供されます。
