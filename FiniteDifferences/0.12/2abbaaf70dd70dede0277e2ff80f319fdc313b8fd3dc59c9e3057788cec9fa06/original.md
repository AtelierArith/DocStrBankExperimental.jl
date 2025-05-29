```
extrapolate_fdm(
    m::FiniteDifferenceMethod,
    f,
    x::Real,
    initial_step::Real=10,
    power::Int=1,
    breaktol::Real=Inf,
    kw_args...
)
```

Use Richardson extrapolation to extrapolate a finite difference method.

Takes further in keyword arguments for `Richardson.extrapolate`. This method automatically sets `power = 2` if `m` is symmetric and `power = 1`. Moreover, it defaults `breaktol = Inf`.

# Arguments

  * `m::FiniteDifferenceMethod`: Finite difference method to estimate the step size for.
  * `f`: Function to evaluate the derivative of.
  * `x::Real`: Point to estimate the derivative at.
  * `initial_step::Real=10`: Initial step size.

# Returns

  * `Tuple{<:AbstractFloat, <:AbstractFloat}`: Estimate of the derivative and error.
