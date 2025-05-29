```
radius_graph(points::AbstractMatrix, 
             r::AbstractFloat; 
             graph_indicator = nothing,
             self_loops = false, 
             dir = :in, 
             kws...)
```

与えられた距離 `r` 内の隣接ノードに各ノードがリンクされたグラフを作成します。  

# 引数

  * `points`: ノードのユークリッド位置を格納する num*features × num*nodes 行列。
  * `r`: 半径。
  * `graph_indicator`: 何も指定しないか、各ノードのグラフ割り当てを含むベクトル。この場合、返されるグラフはグラフのバッチになります。
  * `self_loops`: `true` の場合、ノード自身を隣接ノードの中に含め、その場合グラフには自己ループが含まれます。
  * `dir`: エッジの方向。`dir=:in` の場合、エッジは隣接ノードから中心ノードに向かいます。`dir=:out` の場合は逆の方向になります。
  * `kws`: さらなるキーワード引数は [`GNNGraph`](@ref) コンストラクタに渡されます。

# 例

```julia
julia> n, r = 10, 0.75;

julia> x = rand(Float32, 3, n);

julia> g = radius_graph(x, r)
GNNGraph:
    num_nodes = 10
    num_edges = 46

julia> graph_indicator = [1,1,1,1,1,2,2,2,2,2];

julia> g = radius_graph(x, r; graph_indicator)
GNNGraph:
    num_nodes = 10
    num_edges = 20
    num_graphs = 2
```

# 参考文献

論文 [Dynamic Hidden-Variable Network Models](https://arxiv.org/pdf/2101.00414.pdf) のセクション B の段落 1 と 2
