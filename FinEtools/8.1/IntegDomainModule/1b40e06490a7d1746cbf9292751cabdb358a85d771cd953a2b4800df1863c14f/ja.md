```
IntegDomain(fes::S, integration_rule::IR) where {S<:AbstractFESet, IR<:AbstractIntegRule}
```

デフォルトの方向行列（単位行列）を使用して構築し、他の次元はデフォルトの1.0とします。
