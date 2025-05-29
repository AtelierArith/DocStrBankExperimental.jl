```
set_models!(sim_inst::SimulationInstance{T}, models::Vector{M}) where {T <: AbstractSimulationData, M <: AbstractModel}
```

Set the `models` to be used by the SimulationDef held by `sim_inst`. 
