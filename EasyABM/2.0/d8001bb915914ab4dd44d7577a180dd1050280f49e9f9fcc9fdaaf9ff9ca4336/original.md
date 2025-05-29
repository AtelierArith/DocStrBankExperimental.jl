```julia
static_simple_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.StaticType, EasyABM.SimGType}}

```

Creates a simple prop graph for adjacency_matrix given as a Sparse Matrix. 
