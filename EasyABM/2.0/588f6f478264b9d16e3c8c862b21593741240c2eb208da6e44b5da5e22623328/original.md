```julia
add_node!(
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}};
    kwargs...
) -> Int64

```

Adds a node with properties specified in `kwargs` to the model's graph.
