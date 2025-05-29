```
ANND(G::T, vs=vertices(G); check_directed::Bool=true) where {T<:Graphs.AbstractGraph}
```

グラフ `G` のすべてのノードに対応する平均最近接隣接度 (ANND) のベクトルを返します。もし `v` が指定されている場合は、`v` のノードに対する ANND のみを返します。ノード `i` の ANND は次のように定義されます。 $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ ここで、$a_{ij}$ は隣接行列 $A$ の行 `i` 列 `j` の要素を示し、$k_i$ はノード `i` の次数を示します。

**注意事項:** 

  * ANND は非ゼロ次数のノードに対してのみ定義されています。もし `degree(G,i) = 0` の場合、`ANND(G,i) = 0` となります。
  * `G` が有向グラフの場合、デフォルトではエラーが発生します。なぜなら、この場合 `degree` 関数はノード `i` の入ってくるエッジと出ていくエッジの合計を返すからです。

このチェックは `check_directed=false` に設定することでオフにできます。このチェックは実際の計算が行われる前にのみ実行されます。

# 例

```jldoctest ANND_graph_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> ANND(G,[10; 20; 30])
3-element Vector{Float64}:
 13.5
 14.0
  9.0

```

```jldoctest ANND_graph_docs
julia> Gd = SimpleDiGraph(G);

julia> ANND(Gd,[10; 20; 30]);
ERROR: ArgumentError: グラフは有向です。次数関数はノード `i` の入ってくるエッジと出ていくエッジの合計を返します。代わりに ANND_in または ANND_out を使用することを検討してください。
[...]
```

```jldoctest ANND_graph_docs
julia> ANND(Gd,[10; 20; 30], check_directed=false)
3-element Vector{Float64}:
 13.5
 14.0
  9.0

```

参照: `ANND_in`, `ANND_out`, [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
