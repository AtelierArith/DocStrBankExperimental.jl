```
solve_dynamic_model(network::Network, releases::Union{Vector{Release},Vector{ProportionalRelease}}, shocks::Vector{TemperatureShockData}, algorithm, tspan)
```

Return ODE model solution for network problem with releases and temperature shocks.
