```
induced_subgraph(graph, nodes)
```

提供された `nodes` を使用して元のグラフからサブグラフを生成します。この関数はノードの隣接ノードを含み、元のグラフで接続されているノード間にエッジを作成します。ノードに隣接ノードがない場合、孤立したノードがサブグラフに追加されます。指定されたノードとその特徴を持つ新しい `GNNGraph` を返します。

# 引数

  * `graph`. ノード、エッジ、およびノードの特徴を含む元の GNNGraph。
  * `nodes``. サブグラフに含めるノードインデックスのベクトル。

# 例

```julia
julia> s = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> t = [2, 3]
2-element Vector{Int64}:
 2
 3

julia> graph = GNNGraph((s, t), ndata = (; x=rand(Float32, 32, 3), y=rand(Float32, 3)), edata = rand(Float32, 2))
GNNGraph:
  num_nodes: 3
  num_edges: 2
  ndata:
        y = 3-element Vector{Float32}
        x = 32×3 Matrix{Float32}
  edata:
        e = 2-element Vector{Float32}

julia> nodes = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> subgraph = Graphs.induced_subgraph(graph, nodes)
GNNGraph:
  num_nodes: 2
  num_edges: 1
  ndata:
        y = 2-element Vector{Float32}
        x = 32×2 Matrix{Float32}
  edata:
        e = 1-element Vector{Float32}
```
