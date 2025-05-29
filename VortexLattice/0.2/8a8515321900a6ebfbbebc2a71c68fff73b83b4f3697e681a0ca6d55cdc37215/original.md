```
lifting_line_coefficients(system, r, c; frame=Body())
```

Return the force and moment coefficients (per unit span) for each spanwise segment of a lifting line representation of the geometry.

This function requires that a near-field analysis has been performed on `system` to obtain panel forces.

# Arguments

  * `system`: Object of type [`System`](@ref) that holds precalculated  system properties.
  * `r`: Vector with length equal to the number of surfaces, with each element  being a matrix with size (3, ns+1) which contains the x, y, and z coordinates  of the resulting lifting line coordinates
  * `c`: Vector with length equal to the number of surfaces, with each element  being a vector of length `ns+1` which contains the chord lengths at each  lifting line coordinate.

# Keyword Arguments

  * `frame`: frame in which to return `cf` and `cm`, possible options are  [`Body()`](@ref) (default), [`Stability()`](@ref), and [`Wind()`](@ref)`

# Return Arguments:

  * `cf`: Vector with length equal to the number of surfaces, with each element  being a matrix with size (3, ns) which contains the x, y, and z direction  force coefficients (per unit span) for each spanwise segment.
  * `cm`: Vector with length equal to the number of surfaces, with each element  being a matrix with size (3, ns) which contains the x, y, and z direction  moment coefficients (per unit span) for each spanwise segment.
