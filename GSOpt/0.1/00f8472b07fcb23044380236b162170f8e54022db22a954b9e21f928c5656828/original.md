```
Variable information structure for GP and SP variables.
```

Contains common fields shared between GPVariable and SPVariable.

# Fields

  * `index::Int`: Unique identifier for the variable within the model
  * `name::String`: Variable name
  * `lower_bound::Union{Float64,Nothing}`: Lower bound (must be positive if specified)
  * `upper_bound::Union{Float64,Nothing}`: Upper bound (must be positive if specified)
  * `fixed_value::Union{Float64,Nothing}`: Fixed value (must be positive if specified)
