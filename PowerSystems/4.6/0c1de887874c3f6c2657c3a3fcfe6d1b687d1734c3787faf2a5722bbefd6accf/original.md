```julia
mutable struct StorageCost <: PowerSystems.OperationalCost
```

  * `charge_variable_cost::InfrastructureSystems.CostCurve`: (default of 0) Variable cost of charging represented as a [`CostCurve`](@ref)
  * `discharge_variable_cost::InfrastructureSystems.CostCurve`: (default of 0) Variable cost of discharging represented as a [`CostCurve`](@ref)
  * `fixed::Float64`: (default: 0) Fixed cost of operating the storage system
  * `start_up::Union{Float64, @NamedTuple{charge::Float64, discharge::Float64}}`: (default: 0) Start-up cost
  * `shut_down::Float64`: (default: 0) Shut-down cost
  * `energy_shortage_cost::Float64`: (default: 0) Cost incurred by the model for being short of the energy target
  * `energy_surplus_cost::Float64`: (default: 0) Cost incurred by the model for surplus energy stored

```
StorageCost(charge_variable_cost, discharge_variable_cost, fixed, start_up, shut_down, energy_shortage_cost, energy_surplus_cost)
StorageCost(; charge_variable_cost, discharge_variable_cost, fixed, start_up, shut_down, energy_shortage_cost, energy_surplus_cost)
```

An operational cost for storage units including fixed costs and variable costs to charge or discharge.

This data structure is not intended to represent market storage systems market operations like the submission of buy/sell bids – see [`MarketBidCost`](@ref) instead.
