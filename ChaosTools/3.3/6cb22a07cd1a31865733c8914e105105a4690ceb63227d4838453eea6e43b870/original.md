```
orbitdiagram(ds::DynamicalSystem, i, p_index, pvalues; kwargs...) → od
```

Compute the orbit diagram (sometimes wrongly called bifurcation diagram) of the given dynamical system, saving the `i` variable(s) for parameter values `pvalues`. The `p_index` specifies which parameter to change via `set_parameter!(ds, p_index, pvalue)`. Works for any kind of `DynamicalSystem`, although it mostly makes sense with one of `DeterministicIteratedMap, StroboscopicMap, PoincareMap`.

An orbit diagram is simply a collection of the last `n` states of `ds` as `ds` is evolved. This is done for each parameter value.

`i` can be `Int` or `AbstractVector{Int}`. If `i` is `Int`, `od` is a vector of vectors. Else `od` is a vector of vectors of vectors. Each entry od `od` are the points at each parameter value, so that `length(od) == length(pvalues)` and `length(od[j]) == n, ∀ j`.

## Keyword arguments

  * `n::Int = 100`: Amount of points to save for each parameter value.
  * `Δt = 1`: Stepping time between saving points.
  * `u0 = nothing`: Specify an initial state. If `nothing`, the previous state after each parameter is used to seed the new initial condition at the new parameter (with the very first state being the system's state). This makes convergence to the attractor faster, necessitating smaller `Ttr`. Otherwise `u0` can be a standard state, or a vector of states, so that a specific state is used for each parameter.
  * `Ttr::Int = 10`: Each orbit is evolved for `Ttr` first before saving output.
  * `ulims = (-Inf, Inf)`: only record system states within `ulims` (only valid if `i isa Int`). Iteration continues until `n` states fall within `ulims`.
  * `show_progress = false`: Display a progress bar (counting the parameter values).
  * `periods = nothing`: Only valid if `ds isa StroboscopicMap`. If given, it must be a a container with same layout as `pvalues`. Provides a value for the `period` for each parameter value. Useful in case the orbit diagram is produced versus a driving frequency.
