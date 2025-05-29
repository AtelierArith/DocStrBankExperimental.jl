```
batch(gs::Vector{<:GNNGraph})
```

複数の `GNNGraph` を1つにバッチ処理し、元のノードとエッジの合計数を含む単一のグラフを作成します。

[`SparseArrays.blockdiag`](@ref) と同等です。さらに [`MLUtils.unbatch`](@ref) も参照してください。

# 例

```jldoctest
julia> g1 = rand_graph(4, 4, ndata=ones(Float32, 3, 4))
GNNGraph:
  num_nodes: 4
  num_edges: 4
  ndata:
    x = 3×4 Matrix{Float32}

julia> g2 = rand_graph(5, 4, ndata=zeros(Float32, 3, 5))
GNNGraph:
  num_nodes: 5
  num_edges: 4
  ndata:
    x = 3×5 Matrix{Float32}

julia> g12 = MLUtils.batch([g1, g2])
GNNGraph:
  num_nodes: 9
  num_edges: 8
  num_graphs: 2
  ndata:
    x = 3×9 Matrix{Float32}

julia> g12.ndata.x
3×9 Matrix{Float32}:
 1.0  1.0  1.0  1.0  0.0  0.0  0.0  0.0  0.0
 1.0  1.0  1.0  1.0  0.0  0.0  0.0  0.0  0.0
 1.0  1.0  1.0  1.0  0.0  0.0  0.0  0.0  0.0
```
