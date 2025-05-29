```
DBCM(G::T; precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
DBCM(;d_out::Vector{T}, d_in::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

`DBCM`型のコンストラクタ関数。

デフォルトでは、グラフタイプ `T` に応じて、$Graphs.jl$ からの入次数と出次数の定義が適用されます。異なる次数の定義を使用したい場合は、次数のシーケンスのベクトルをキーワード引数（`d_out`, `d_in`）として渡すことができます。基盤となるグラフなしで次数のシーケンスから直接モデルを生成したい場合は、単に次数のシーケンスを引数（`d_out`, `d_in`）として渡すことができます。隣接行列やエッジリストから作業したい場合は、$JuliaGraphs$ エコシステムのグラフコンストラクタを使用できます。

# 例

```jldoctest DBCM_creation
# グラフからモデルを生成する
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques())
{16, 111} 有向単純 Int64 グラフ
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (16 頂点, 15 ユニーク次数ペア, 0.94 圧縮比)
```

```jldoctest DBCM_creation
# 次数シーケンスから直接モデルを生成する
julia> model = DBCM(d_out=MaxEntropyGraphs.Graphs.outdegree(G), d_in=MaxEntropyGraphs.Graphs.indegree(G))
DBCM{Nothing, Float64} (16 頂点, 15 ユニーク次数ペア, 0.94 圧縮比)
```

```jldoctest DBCM_creation
# 異なる精度で次数シーケンスから直接モデルを生成する
julia>  model = DBCM(d_out=MaxEntropyGraphs.Graphs.outdegree(G), d_in=MaxEntropyGraphs.Graphs.indegree(G), precision=Float32)
DBCM{Nothing, Float32} (16 頂点, 15 ユニーク次数ペア, 0.94 圧縮比)
```

```jldoctest DBCM_creation
# 隣接行列からモデルを生成する
julia> A = [0 1 1;1 0 0;1 1 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(A)
{3, 5} 有向単純 Int64 グラフ
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (3 頂点, 3 ユニーク次数ペア, 1.00 圧縮比)
```

```jldoctest DBCM_creation
# エッジリストからモデルを生成する
julia> E = [(1,2),(1,3),(2,3)];

julia> edgelist = [MaxEntropyGraphs.Graphs.Edge(x,y) for (x,y) in E];

julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraphFromIterator(edgelist)
{3, 3} 有向単純 Int64 グラフ
julia> model = DBCM(G)
DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (3 頂点, 3 ユニーク次数ペア, 1.00 圧縮比)

```

[`Graphs.outdegree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.outdegree-Tuple{AbstractGraph,%20Integer})、[`Graphs.indegree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.indegree-Tuple{AbstractGraph,%20Integer}) も参照してください。
