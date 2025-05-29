```
IntegDomain(
    fes::S,
    integration_rule::IR,
    otherdimension::F,
) where {S<:AbstractFESet, IR<:AbstractIntegRule, F<:Function}
```

Construct with the default orientation matrix (identity), and  other dimension provided by a function.
