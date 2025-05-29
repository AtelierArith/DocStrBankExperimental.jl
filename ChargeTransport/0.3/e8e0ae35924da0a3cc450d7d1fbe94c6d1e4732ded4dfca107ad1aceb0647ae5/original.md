```julia
reaction!(
    f,
    u,
    node,
    data,
    _::Type{ChargeTransport.InEquilibrium}
)

```

Reaction in case of equilibrium, i.e. no generation and recombination is considered.
