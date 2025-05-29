```julia
static_dir_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.StaticType, EasyABM.DirGType}}

```

Creates a directed prop graph for adjacency matrix given as a Sparse Matrix. 
