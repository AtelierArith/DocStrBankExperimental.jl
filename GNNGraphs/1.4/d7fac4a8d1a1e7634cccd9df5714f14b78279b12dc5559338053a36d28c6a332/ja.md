```
mldataset2gnngraph(dataset)
```

パッケージ MLDatasets.jl からグラフデータセットを1つまたは複数の [`GNNGraph`](@ref) に変換します。

# 例

```jldoctest
julia> using MLDatasets, GNNGraphs

julia> mldataset2gnngraph(Cora())
GNNGraph:
  num_nodes: 2708
  num_edges: 10556
  ndata:
    val_mask = 2708-element BitVector
    targets = 2708-element Vector{Int64}
    test_mask = 2708-element BitVector
    features = 1433×2708 Matrix{Float32}
    train_mask = 2708-element BitVector
```
