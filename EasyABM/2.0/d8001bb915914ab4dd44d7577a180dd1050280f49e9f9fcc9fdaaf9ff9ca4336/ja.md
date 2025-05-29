```julia
static_simple_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.StaticType, EasyABM.SimGType}}

```

与えられた隣接行列に対して、単純なプロップグラフを作成します。
