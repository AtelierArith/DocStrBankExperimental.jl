```
solInterpolated(sol::Sol{T,O},index::Int,step::Float64) where {T,O}
```

Constructs a new solution by interpolating the current solution at each step for one variable.

# Arguments

  * `sol::Sol{T,O}`: The solution struct.
  * `index::Int`: the index of the variable to interpolate.
  * `step::Float64`: the step size at which to generate the new solution.

# Returns

  * A new solution that contains the information of one variable at each step size.
