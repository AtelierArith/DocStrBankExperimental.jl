```
add_edge!(model::ABM{<:GraphSpace},  args...; kwargs...)
```

Add a new edge (relationship between two positions) to the graph. Returns a boolean, true if the operation was successful.

`args` and `kwargs` are directly passed to the `add_edge!` dispatch that acts the underlying graph type.
