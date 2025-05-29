```
solve_dynamic_model(node::Node, releases::Union{Vector{Release},Vector{ProportionalRelease}}, shocks::TemperatureShockData, algorithm, tspan)
```

Return ODE model solution for single node problem with releases and temperature shocks.
