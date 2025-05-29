```
DurationHorizons{T} <: AbstractHorizons{T}
```

Type used for specifiying the optimization and implementation horizon of a receding horizon model as the duration of the horizons. This implies that the number of operational periods in the different iterations can vary.

Iterating a `DurationHorizons` results in `SingleHorizon` which includes all information required for a single run.

# Fields

  * **`len::Int64`** is the total length of the investigated timeframe as a multiple of the duration of 1 of an operational period.
  * **`dur::Vector{T}`** is a vector of the duration of each individual operational period.
  * **`optim::Int64`** is the sum of the ***duration*** of the operational periods that are used in the ***optimization*** horizon.
  * **`impl::Int64`** is the sum of the ***duration*** of the operational periods that are used in the ***implementation*** horizon.

!!! note "Optimization and implementation horizon"
    The optimization horizon corresponds to the horizon used in each individual optimization run while the implementation horizon must be shorter than the optimization horizon. This is enforced through an inner constructor. It corresponds to the operational periods extracted from the model run.

