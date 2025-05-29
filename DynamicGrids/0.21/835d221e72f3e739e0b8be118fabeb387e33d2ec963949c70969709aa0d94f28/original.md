```
SetNeighborhoodRule <: SetRule
```

A [`SetRule`](@ref) that only writes to its neighborhood, and does not need to bounds-check.

[`positions`](@ref) and [`offsets`](@ref) are useful iterators for modifying neighborhood values. 

`SetNeighborhoodRule` rules must return a [`Neighborhood`](@ref) object from the function  `neighborhood(rule)`. By default this is `rule.neighborhood`. If this property exists,  no interface methods are required.
