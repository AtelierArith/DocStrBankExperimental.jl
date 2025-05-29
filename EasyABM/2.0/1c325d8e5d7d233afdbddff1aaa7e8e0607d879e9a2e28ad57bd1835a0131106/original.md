```julia
dynamic_simple_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.MortalType, EasyABM.SimGType}}

```

Creates a simple prop graph for adjacency_matrix given as a Sparse Matrix. 
