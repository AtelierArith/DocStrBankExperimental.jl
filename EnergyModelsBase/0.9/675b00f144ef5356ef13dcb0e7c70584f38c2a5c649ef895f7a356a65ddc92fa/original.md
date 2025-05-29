```
has_capacity(n::Node)
```

Checks whether node `n` has a standard capacity.

By default, [`Storage`](@ref) and [`Availability`](@ref) nodes are excluded as they either have multiple capacities (`Storage`) or non (`Availability`).
