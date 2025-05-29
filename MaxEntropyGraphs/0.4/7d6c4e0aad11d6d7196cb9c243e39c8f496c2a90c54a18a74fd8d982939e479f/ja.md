```
UBCM(G::T; d::Vector=Graphs.degree(G), precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
UBCM(d::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

`UBCM`型のコンストラクタ関数。

デフォルトでは、グラフのタイプ `T` に応じて `Graphs.jl` の次数の定義が適用されます。異なる次数の定義を使用したい場合は、2番目の引数として次数のベクトルを渡すことができます。基盤となるグラフなしで次数列から直接モデルを生成したい場合は、次数列を引数として渡すだけで済みます。隣接行列やエッジリストから作業したい場合は、`JuliaGraphs` エコシステムのグラフコンストラクタを使用できます。

# 例

```jldoctest
# グラフからモデルを生成する
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate)
{34, 78} 無向単純 Int64 グラフ
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (34 頂点, 11 ユニーク次数, 0.32 圧縮比)
```

```jldoctest
# 次数列から直接モデルを生成する
julia> model = UBCM(d=[4;3;3;3;2])
UBCM{Nothing, Float64} (5 頂点, 3 ユニーク次数, 0.60 圧縮比)
```

```jldoctest
# 異なる精度で次数列から直接モデルを生成する
julia> model = UBCM(d=[4;3;3;3;2], precision=Float16)
UBCM{Nothing, Float16} (5 頂点, 3 ユニーク次数, 0.60 圧縮比)
```

```jldoctest
# 隣接行列からモデルを生成する
julia> A = [0 1 1;1 0 0;1 0 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(A)
{3, 2} 無向単純 Int64 グラフ
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 頂点, 2 ユニーク次数, 0.67 圧縮比)
```

```jldoctest
# エッジリストからモデルを生成する
julia> E = [(1,2),(1,3),(2,3)];

julia> edgelist = [MaxEntropyGraphs.Graphs.Edge(x,y) for (x,y) in E];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraphFromIterator(edgelist)
{3, 3} 無向単純 Int64 グラフ
julia> model = UBCM(G)
UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 頂点, 1 ユニーク次数, 0.33 圧縮比)
```

[`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)、[`SimpleWeightedGraphs.inneighbors`](https://juliagraphs.org/SimpleWeightedGraphs.jl/stable/api/#Graphs.inneighbors-Tuple{SimpleWeightedDiGraph,%20Integer}) も参照してください。
