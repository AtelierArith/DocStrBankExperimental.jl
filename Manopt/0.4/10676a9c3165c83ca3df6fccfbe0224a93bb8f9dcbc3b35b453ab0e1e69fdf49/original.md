```
StopWhenPopulationDiverges{TParam<:Real} <: StoppingCriterion
```

Stop if `σ` times maximum deviation increased by more than `tol`. This usually indicates a far too small `σ`, or divergent behavior. This corresponds to `TolXUp` condition from [Hansen:2023](@cite).
