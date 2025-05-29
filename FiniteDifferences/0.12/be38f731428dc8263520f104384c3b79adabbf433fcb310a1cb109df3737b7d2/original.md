```
forward_fdm(
    p::Int,
    q::Int;
    adapt::Int=1,
    condition::Real=DEFAULT_CONDITION,
    factor::Real=DEFAULT_FACTOR,
    max_range::Real=Inf,
    geom::Bool=false
)
```

Contruct a finite difference method at a forward grid of `p` points.

# Arguments

  * `p::Int`: Number of grid points.
  * `q::Int`: Order of the derivative to estimate.

# Keywords

  * `adapt::Int=1`: Use another finite difference method to estimate the magnitude of the   `p`th order derivative, which is important for the step size computation. Recurse   this procedure `adapt` times.
  * `condition::Real`: Condition number. See [`DEFAULT_CONDITION`](@ref).
  * `factor::Real`: Factor number. See [`DEFAULT_FACTOR`](@ref).
  * `max_range::Real=Inf`: Maximum distance that a function is evaluated from the input at   which the derivative is estimated.
  * `geom::Bool`: Use geometrically spaced points instead of linearly spaced points.

# Returns

  * `FiniteDifferenceMethod`: The specified finite difference method.
