```julia
dynamic_simple_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.MortalType, EasyABM.SimGType}}

```

与えられた隣接行列のための単純なプロップグラフを作成します。
