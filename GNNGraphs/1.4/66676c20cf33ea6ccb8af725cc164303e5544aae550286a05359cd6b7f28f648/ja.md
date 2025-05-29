```
knn_graph(points::AbstractMatrix, 
          k::Int; 
          graph_indicator = nothing,
          self_loops = false, 
          dir = :in, 
          kws...)
```

各ノードがその `k` 最も近い `points` にリンクされる `k`-最近傍グラフを作成します。  

# 引数

  * `points`: ノードのユークリッド位置を格納する num*features × num*nodes 行列。
  * `k`: kNNアルゴリズムで考慮される隣接点の数。
  * `graph_indicator`: 何も指定しないか、各ノードのグラフ割り当てを含むベクトル。                     この場合、返されるグラフはグラフのバッチになります。
  * `self_loops`: `true` の場合、ノード自身をその `k` 最近傍の中に含め、               この場合、グラフには自己ループが含まれます。
  * `dir`: エッジの方向。`dir=:in` の場合、エッジは `k` 隣接点から中央ノードに向かいます。`dir=:out` の場合、逆の方向になります。
  * `kws`: さらなるキーワード引数は [`GNNGraph`](@ref) コンストラクタに渡されます。

# 例

```julia
julia> n, k = 10, 3;

julia> x = rand(Float32, 3, n);

julia> g = knn_graph(x, k)
GNNGraph:
    num_nodes = 10
    num_edges = 30

julia> graph_indicator = [1,1,1,1,1,2,2,2,2,2];

julia> g = knn_graph(x, k; graph_indicator)
GNNGraph:
    num_nodes = 10
    num_edges = 30
    num_graphs = 2
```
