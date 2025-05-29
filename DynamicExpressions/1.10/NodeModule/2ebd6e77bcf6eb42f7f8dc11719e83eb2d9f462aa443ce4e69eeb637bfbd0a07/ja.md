```
filter_map!(filter_fnc::Function, map_fnc::Function, stack::Vector{GT}, tree::AbstractNode)
```

[`filter_map`](@ref) と同等ですが、結果を事前に確保された配列に格納します。
