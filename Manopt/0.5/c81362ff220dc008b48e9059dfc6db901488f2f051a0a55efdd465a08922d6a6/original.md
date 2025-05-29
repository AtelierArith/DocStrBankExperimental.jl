```
is_feasible(M::AbstractManifold, cmo::ConstrainedManifoldObjective, p, kwargs...)
```

Evaluate whether a boint `p` on `M` is feasible with respect to the [`ConstrainedManifoldObjective`](@ref) `cmo`. That is for the provided inequality constaints $g: \mathcal M → ℝ^m$ and equality constaints $h: \mathcal M \to ℝ^m$ from within `cmo`, the point $p ∈ \mathcal M$ is feasible if

$$
g_i(p) ≤ 0, \text{ for all } i=1,…,m\quad\text{ and }\quad h_j(p) = 0, \text{ for all } j=1,…,n.
$$

# Keyword arguments

  * `check_point::Bool=true`: whether to also verify that ``p∈\mathcal M` holds, using [`is_point`](@extref ManifoldsBase :jl:method:`ManifoldsBase.is_point-Tuple{AbstractManifold, Any, Bool}`)
  * `error::Symbol=:none`: if the point is not feasible, this symbol determines how to report the error.

      * `:error`: throws an error
      * `:info`: displays the error message as an @info
      * `:none`: (default) the function just returns true/false
      * `:warn`: displays the error message as a @warning.

The keyword `error=` and all other `kwargs...` are passed on to [`is_point`](@extref ManifoldsBase :jl:method:`ManifoldsBase.is_point-Tuple{AbstractManifold, Any, Bool}`) if the point is verfied (see `check_point`).

All other keywords are passed on to `is_poi`
