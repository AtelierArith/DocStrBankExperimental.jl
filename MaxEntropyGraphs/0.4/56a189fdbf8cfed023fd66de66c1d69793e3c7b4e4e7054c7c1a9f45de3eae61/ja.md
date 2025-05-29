```
ANND(A::T, i::Int; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
```

隣接行列 `A` を使用してノード `i` の平均最近接隣人度 (ANND) を計算します。ノード `i` の ANND は $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ と定義され、ここで $a_{ij}$ は行列 `A` の行 `i` と列 `j` の要素を示し、$k_i$ はノード `i` の次数を示します。

**注意:**

  * この関数は `::AbstractMaxEntropyModel` モデルの期待される隣接行列での使用を意図しています。`::AbstractGraph` オブジェクト用の別のメソッドがあります。
  * `A` が対称でない場合、あなたは有向グラフを持っており、デフォルトではエラーが発生します。これは `check_directed=false` を設定することで無効にできます。
  * 隣接行列は正方行列である必要があります。そうでない場合、デフォルトではエラーが発生します。これは `check_dimensions=false` を設定することで無効にできます。

# 例

```jldoctest ANND_mat_node_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> A = adjacency_matrix(G);

julia> ANND(A, 1)
4.3125

```

```jldoctest ANND_mat_node_docs
julia> Gd = SimpleDiGraph(G);

julia> add_vertex!(Gd); add_edge!(Gd, 1, nv(Gd));

julia> Ad = adjacency_matrix(Gd);

julia> ANND(Ad, 1)
ERROR: ArgumentError: The matrix is not symmetrical. Consider using ANND_in or ANND_out instead.
[...]
```

```jldoctest ANND_mat_node_docs
julia> ANND(Ad, 1, check_directed=false)
4.375

```

```jldoctest ANND_mat_node_docs
julia> ANND(rand(2,3),1)
ERROR: DimensionMismatch: `A` must be a square matrix.
[...]
```

参照: `ANND_in`, `ANND_out`, [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
