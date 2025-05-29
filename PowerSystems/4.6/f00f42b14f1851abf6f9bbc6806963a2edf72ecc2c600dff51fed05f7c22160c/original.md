```julia
mutable struct ThermalGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.ProductionVariableCostCurve`: Variable production cost. Can take a [`CostCurve`](@ref) or [`FuelCurve`](@ref)
  * `fixed::Float64`: Fixed cost of keeping the unit online. For some cost represenations this field can be     duplicative
  * `start_up::Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}`: Start-up cost can take linear or multi-stage cost
  * `shut_down::Float64`: Cost to turn the unit off

```
ThermalGenerationCost(variable, fixed, start_up, shut_down)
ThermalGenerationCost(; variable, fixed, start_up, shut_down)
```

An operational cost for thermal generators which includes fixed cost, variable cost, shut-down cost, and  multiple options for start up costs.
