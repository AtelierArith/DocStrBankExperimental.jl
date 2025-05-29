```
solInterpolated(sol::Sol{T,O},step::Float64) where {T,O}
```

Construct a new solution by interpolating the current solution at each step for all variables.

# Arguments

  * `sol::Sol{T,O}`: The solution struct.
  * `step::Float64`: the step size at which to generate the new solution.

# Returns

  * A new solution that contains information at each step size..
