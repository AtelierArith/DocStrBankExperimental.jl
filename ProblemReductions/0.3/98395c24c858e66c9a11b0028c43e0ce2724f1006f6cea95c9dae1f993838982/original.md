```
flavors(::Type{<:AbstractProblem}) -> UnitRange
flavors(::GT) where GT<:AbstractProblem -> UnitRange
```

Returns a vector of integers as the flavors (domain) of a degree of freedom.

!!! warning
    Flavors is defined a `0:num_flavors-1`. To access the previous version of the flavors, use [`flavor_names`](@ref).

