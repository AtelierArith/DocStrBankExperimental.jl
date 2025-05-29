```julia
dynamic_dir_graph(
    g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.MortalType, EasyABM.DirGType}}

```

Creates a directed prop graph for a given directed graph created with Graphs.jl. 
