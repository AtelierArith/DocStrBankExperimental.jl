```
addconstraint!(P::AbstractHPolygon, constraint::HalfSpace;
               [linear_search]::Bool=length(P.constraints) < 10,
               [prune]::Bool=true)
```

Add a linear constraint to a polygon in constraint representation, keeping the constraints sorted by their normal directions.

### Input

  * `P`             – polygon in constraint representation
  * `constraint`    – linear constraint to add
  * `linear_search` – (optional, default:                    `length(constraints) < 10`) flag to                    choose between linear and binary search
  * `prune`         – (optional, default: `true`) flag for removing redundant                    constraints in the end
