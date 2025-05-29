```
StopWhenPopulationStronglyConcentrated{TParam<:Real} <: StoppingCriterion
```

Stop if the standard deviation in all coordinates is smaller than `tol` and norm of `σ * p_c` is smaller than `tol`. This corresponds to `TolX` condition from [Hansen:2023](@cite).

# Fields

  * `tol` the tolerance to check against
  * `at_iteration` an internal field to indicate at with iteration $i \geq 0$ the tolerance was met.

# Constructor

```
StopWhenPopulationStronglyConcentrated(tol::Real)
```
