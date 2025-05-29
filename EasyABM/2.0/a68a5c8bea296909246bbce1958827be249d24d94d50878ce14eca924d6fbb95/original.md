```julia
create_graph_model(
    agents::Array{EasyABM.GraphAgent{A<:EasyABM.MType, B<:EasyABM.MType}, 1},
    graph::EasyABM.AbstractPropGraph{S<:EasyABM.MType, G<:EasyABM.GType};
    agents_type,
    graphics,
    random_positions,
    vis_space,
    kwargs...
) -> Union{Nothing, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.DirGType} where S<:EasyABM.MType, EasyABM.GraphModel{S, EasyABM.StaticType, EasyABM.SimGType} where S<:EasyABM.MType}

```

Creates a model with 

  * `agents` : list of agents.
  * `graph`  : A graph created with Graphs.jl and converted to EasyABM graph type Or created directly using EasyABM graph functionality.
  * `graphics` : if true properties of pos, shape, color, orientation will be assigned to each agent by default, if not already assigned by user.
  * `agents_type` : Set it to Static if number of agents is fixed during model run. Otherwise set it to Mortal.
  * `random_positions` : If this property is true, each agent will be assigned a random node on the graph.
  * `kwargs` : Keyword argments used as model properties.
