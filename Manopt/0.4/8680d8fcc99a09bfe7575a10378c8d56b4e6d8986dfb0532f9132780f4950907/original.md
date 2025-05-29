```
StopWhenPopulationCostConcentrated{TParam<:Real} <: StoppingCriterion
```

Stop if the range of the best objective function value in the last `max_size` generations and all function values in the current generation is below `tol`. This corresponds to `TolFun` condition from [Hansen:2023](@cite).

# Constructor

```
StopWhenPopulationCostConcentrated(tol::Real, max_size::Int)
```
