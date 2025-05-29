```
ANND(G::T, i::Int; check_directed::Bool=true) where {T<:Graphs.AbstractGraph}
```

グラフ `G` のノード `i` の平均最近接隣接度 (ANND) を計算します。ノード `i` の ANND は $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ と定義され、ここで $a_{ij}$ は隣接行列 $A$ の行 `i` と列 `j` の要素を示し、$k_i$ はノード `i` の次数を示します。

**注意:**

  * ANND は次数がゼロでないノードに対してのみ定義されています。もし `degree(G,i) = 0` であれば、`ANND(G,i) = 0` となります。
  * `G` が有向グラフの場合、デフォルトではエラーが発生します。なぜなら、この場合 `degree` 関数はノード `i` の入ってくるエッジと出ていくエッジの合計を返すからです。このチェックは `check_directed=false` に設定することで無効にできます。

# 例

```jldoctest ANND_graph_node_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> ANND(G,1)
4.3125

```

```jldoctest ANND_graph_node_docs
julia> add_vertex!(G);

julia> ANND(G, nv(G))
0.0
```

```jldoctest ANND_graph_node_docs
julia> Gd = SimpleDiGraph(G);

julia> ANND(Gd,1)
ERROR: ArgumentError: The graph is directed. The degree function returns the incoming plus outgoing edges for node `i`. Consider using ANND_in or ANND_out instead.
[...]
```

```jldoctest ANND_graph_node_docs
julia> ANND(Gd,1, check_directed=false)
4.3125
```

参照: [`ANND_in`](@ref), [`ANND_out`](@ref), [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
