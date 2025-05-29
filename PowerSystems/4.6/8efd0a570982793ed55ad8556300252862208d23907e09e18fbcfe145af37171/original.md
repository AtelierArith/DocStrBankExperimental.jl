```julia
mutable struct RenewableGenerationCost <: PowerSystems.OperationalCost
```

  * `variable::InfrastructureSystems.CostCurve`: Variable cost represented as a [`CostCurve`](@ref)
  * `curtailment_cost::InfrastructureSystems.CostCurve`: (default of 0) Cost of curtailing power represented as a [`CostCurve`](@ref)

```
RenewableGenerationCost(variable, curtailment_cost)
RenewableGenerationCost(variable; curtailment_cost)
RenewableGenerationCost(; variable, curtailment_cost)
```

An operational cost of renewable generators which includes the variable cost of energy (like a [PPA](@ref P)) and the cost of curtailing power. For example, curtailment costs can be used to represent the loss of tax incentives.

The `variable` cost is a required parameter, but `zero(CostCurve)` can be used to set it to 0.
