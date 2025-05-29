```
body_forces(system; kwargs...)
```

Return the body force coefficients given the panel properties for `surfaces`

Note that this function assumes that a near-field analysis has already been performed to obtain the panel forces.

# Arguments

  * `system`: Object of type [`System`](@ref) which holds system properties

# Keyword Arguments

  * `frame`: frame in which to return `CF` and `CM`, options are [`Body()`](@ref) (default), [`Stability()`](@ref), and [`Wind()`](@ref)`
