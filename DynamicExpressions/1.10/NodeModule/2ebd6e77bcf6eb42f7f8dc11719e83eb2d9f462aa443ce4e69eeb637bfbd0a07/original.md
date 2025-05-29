```
filter_map!(filter_fnc::Function, map_fnc::Function, stack::Vector{GT}, tree::AbstractNode)
```

Equivalent to [`filter_map`](@ref), but stores the results in a preallocated array.
