```julia
mutable struct LoadCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.CostCurve`: Variable cost represented as a [`CostCurve`](@ref)
  * `fixed::Float64`: (default: 0) Fixed cost. For some cost represenations this field can be     duplicative

```
LoadCost(variable, fixed)
LoadCost(; variable, fixed)
```

An operational cost for controllable loads (e.g., InterruptiblePowerLoad), including fixed and variable cost components.

The `variable` cost is a required parameter, but `zero(CostCurve)` can be used to set it to 0.
