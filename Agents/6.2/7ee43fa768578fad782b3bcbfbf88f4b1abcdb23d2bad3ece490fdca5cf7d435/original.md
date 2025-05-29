```
add_vertex!(model::ABM{<:GraphSpace})
```

Add a new node (i.e. possible position) to the model's graph and return it. You can connect this new node with existing ones using [`add_edge!`](@ref).
