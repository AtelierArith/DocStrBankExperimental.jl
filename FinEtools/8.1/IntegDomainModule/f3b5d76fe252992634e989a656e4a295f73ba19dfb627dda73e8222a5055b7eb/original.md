```
IntegDomain(
    fes::S,
    integration_rule::IR,
    axisymmetric::Bool,
    otherdimension::T,
) where {S<:AbstractFESet, IR<:AbstractIntegRule, T<:Number}
```

Construct for axially symmetric models. The other dimension is given as a number.
