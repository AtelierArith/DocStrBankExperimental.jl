```
CombinatorialCuts
```

Factory object for [`CombinatorialCuts`](@ref). Pass to `integer_strategy` in `LShaped.Optimizer` or set the [`IntegerStrategy`](@ref) attribute.

...

# Parameters

  * `lower_bound::AbstractFloat = -1e10`: Set a lower bound on the second-stage objective, removing the need to approximate it.
  * `alternate::Bool = false`: Specify if algorithm should alternate between solving relaxed problems (generating regular optimality cuts) and unrelaxed problems (generating combinatorial cuts)
  * `update_L_every::Integer = 0`: Set the frequency at which the lower bound approximation should be updated. Only approximate once if set to zero.
  * `optimizer = nothing`: Optionally specify an optimizer used to solve auxilliary problems in the `LiftAndProject` or `CuttingPlaneTree` strategies.

...
