```julia
create_graph_model(
    graph::EasyABM.AbstractPropGraph{S<:EasyABM.MType, G<:EasyABM.GType};
    graphics,
    random_positions,
    vis_space,
    kwargs...
) -> Union{Nothing, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.DirGType} where S<:EasyABM.MType, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.SimGType} where S<:EasyABM.MType}

```
