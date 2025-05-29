```
IntegDomain(
    fes::S,
    integration_rule::IR,
    otherdimension::T,
) where {S<:AbstractFESet, IR<:AbstractIntegRule, T<:Number}
```

Construct with the default orientation matrix (identity), and constant other dimension.
