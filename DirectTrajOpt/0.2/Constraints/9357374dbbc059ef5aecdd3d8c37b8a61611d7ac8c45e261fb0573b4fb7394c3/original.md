```
struct EqualityConstraint
```

Represents a linear equality constraint.

# Fields

  * `ts::AbstractArray{Int}`: the time steps at which the constraint is applied
  * `js::AbstractArray{Int}`: the components of the trajectory at which the constraint is applied
  * `vals::Vector{R}`: the values of the constraint
  * `vardim::Int`: the dimension of a single time step of the trajectory
  * `label::String`: a label for the constraint
