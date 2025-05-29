```julia
Data(
    grid,
    numberOfCarriers;
    contactVoltageFunction,
    generationData,
    statfunctions
) -> ChargeTransport.Data{ChargeTransport.StandardFuncSet, T, Vector{Float64}} where T<:Function

```

Simplified constructor for Data which only takes the grid and the numberOfCarriers as argument. Here, all necessary information including the physical parameters, but also some numerical information are located.
