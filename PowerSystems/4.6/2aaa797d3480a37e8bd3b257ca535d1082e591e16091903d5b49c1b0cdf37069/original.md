```julia
mutable struct HydroGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.ProductionVariableCostCurve`: Production variable cost represented by a `FuelCurve`, where the fuel is water,     or a `CostCurve` in currency.
  * `fixed::Float64`: (default: 0) Fixed cost of keeping the unit online. For some cost represenations this     field can be duplicative

```
HydroGenerationCost(variable, fixed)
HydroGenerationCost(; variable, fixed)
```

An operational cost of a hydropower generator which includes fixed and variable cost. Variable costs can be used to represent the cost of curtailment if negative values are used or the opportunity cost of water if the costs are positive. It also supports fuel curves to model specific water intake. 

The `variable` cost is a required parameter, but `zero(CostCurve)` can be used to set it to 0.
