```
StopWhenPopulationConcentrated <: StoppingCriterion
```

A stopping criterion for [`NelderMead`](@ref) to indicate to stop when both

  * the maximal distance of the first to the remaining the cost values and
  * the maximal distance of the first to the remaining the population points

drops below a certain tolerance `tol_f` and `tol_p`, respectively.

# Constructor

```
StopWhenPopulationConcentrated(tol_f::Real=1e-8, tol_x::Real=1e-8)
```
