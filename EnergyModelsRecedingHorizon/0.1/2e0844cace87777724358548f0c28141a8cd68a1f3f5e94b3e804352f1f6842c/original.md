```
struct StorageValueCuts <: FutureValue
```

A collection of multiple `StorageValueCut` that constructs a piecewise linear upper bound on the future value of the stored resource.

## Fields

  * **`id::Any`** is the name/identifier of the `StorageValueCuts`.
  * **`time::Int`** is the time where the cut is valid relative to the start of the operational period.
  * **`weight::Real`** is the weighting of the `StorageValueCuts` in the objective function. For example used if the end time of the optimization arrives between two different `StorageValueCuts`.
  * **`time_weight::Real`** is the weighting of the `StorageValueCuts` in the objective function due to the elapsed time.
  * **`cuts::Vector{StorageValueCut}`** is a vector of all the cuts that are included in the future value description.
