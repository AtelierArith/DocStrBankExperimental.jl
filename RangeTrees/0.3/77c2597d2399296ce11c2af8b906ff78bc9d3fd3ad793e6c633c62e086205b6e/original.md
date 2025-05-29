```
RangeNode
```

An augmented, balanced, binary [interval tree](https://en.wikipedia.org/wiki/Interval_tree#Augmented_tree) of intervals of integers represented as a [UnitRange](@ref).

```jldoctest julia> rn = RangeNode([0:0, 3:40, 10:14, 20:35, 29:98]); # example from Wikipedia page

julia> intersect(40:59, rn) 2-element Vector{UnitRange{Int64}}:  40:40  40:59 ````
