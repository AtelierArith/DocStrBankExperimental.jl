```
IntegDomain(
    fes::S,
    integration_rule::IR,
    axisymmetric::Bool,
) where {S<:AbstractFESet, IR<:AbstractIntegRule}
```

Construct with the default orientation matrix (identity), for axially symmetric models. The other dimension is the default unity (1.0).

This will probably be called when `axisymmetric = true`, since the default is `axisymmetric = false`.
