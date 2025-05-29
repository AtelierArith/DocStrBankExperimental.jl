```
nonstationary_statistics(tpt, horizon; B_to_S::Symbol = :interior, initial_dist = :stat)
```

Compute and return the following statistics in a `NamedTuple`:

  * `density`
  * `reactive_density`
  * `tAB_cdf`

### Arguments

  * `tpt`: The [`TPTProblem`](@ref).
  * `horizon`: The time step at which to cut off the calculation. Note that the `horizon` value does NOT enforce that trajectories leaving A hit B by that time.

### Optional Arguments

  * `initial_dist`: A `Symbol` determining how the initial distribution inside `𝒜` has calculated.

      * `:stat`: The initial distribution is equal to stationary distribution of `𝒫(tpt)` restricted `𝒜`.
      * `:uniform`: A uniform distribution supported on `𝒜`.
