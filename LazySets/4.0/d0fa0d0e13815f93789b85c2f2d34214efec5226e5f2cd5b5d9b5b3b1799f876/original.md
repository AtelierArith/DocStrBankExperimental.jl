```
addconstraint!(constraints::Vector{<:HalfSpace}, new_constraint::HalfSpace;
               [linear_search]::Bool=length(P.constraints) < 10,
               [prune]::Bool=true)
```

Add a linear constraint to a sorted vector of constrains, keeping the constraints sorted by their normal directions.

### Input

  * `constraints`    – vector of linear constraints
  * `new_constraint` – linear constraint to add
  * `linear_search`  – (optional, default:                     `length(constraints) < 10`) flag to                     choose between linear and binary search
  * `prune`          – (optional, default: `true`) flag for removing redundant                     constraints in the end

### Algorithm

If `prune` is active, we check if the new constraint is redundant. If the constraint is not redundant, we perform the same check to the left and to the right until we find the first constraint that is not redundant.
