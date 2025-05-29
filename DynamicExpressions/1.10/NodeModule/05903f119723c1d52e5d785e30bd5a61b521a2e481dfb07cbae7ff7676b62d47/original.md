```
filter_map(filter_fnc::Function, map_fnc::Function, tree::AbstractNode, result_type::Type, break_sharing::Val=Val(false))
```

A faster equivalent to `map(map_fnc, filter(filter_fnc, tree))` that avoids the intermediate allocation. However, using this requires specifying the `result_type` of `map_fnc` so the resultant array can be preallocated.
