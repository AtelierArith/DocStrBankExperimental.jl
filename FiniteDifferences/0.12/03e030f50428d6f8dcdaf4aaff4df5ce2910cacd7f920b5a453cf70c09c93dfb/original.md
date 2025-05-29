```
FiniteDifferenceMethod(
    grid::AbstractVector{Int},
    q::Int;
    condition::Real=DEFAULT_CONDITION,
    factor::Real=DEFAULT_FACTOR,
    max_range::Real=Inf
)
```

Construct a finite difference method.

# Arguments

  * `grid::Vector{Int}`: The grid. See [`AdaptedFiniteDifferenceMethod`](@ref) or   [`UnadaptedFiniteDifferenceMethod`](@ref).
  * `q::Int`: Order of the derivative to estimate.

# Keywords

  * `condition::Real`: Condition number. See [`DEFAULT_CONDITION`](@ref).
  * `factor::Real`: Factor number. See [`DEFAULT_FACTOR`](@ref).
  * `max_range::Real=Inf`: Maximum distance that a function is evaluated from the input at   which the derivative is estimated.

# Returns

  * `FiniteDifferenceMethod`: Specified finite difference method.
