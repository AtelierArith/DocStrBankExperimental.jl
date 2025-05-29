```julia
create_edge!(
    edge,
    model::Union{EasyABM.GraphModel{EasyABM.MortalType, EasyABM.MortalType}, EasyABM.GraphModel{EasyABM.MortalType, EasyABM.StaticType}};
    kwargs...
)

```

Adds an edge with properties `kwargs` to model graph. 
