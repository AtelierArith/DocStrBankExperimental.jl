```
BiCM(G::T; precision::N=Float64, kwargs...) where {T<:Graphs.AbstractGraph, N<:Real}
BiCM(;d⊥::Vector{T}, d⊤::Vector{T}, precision::Type{<:AbstractFloat}=Float64, kwargs...)
```

`BiCM`型のコンストラクタ関数。提供するグラフは二部グラフである必要があります。

デフォルトでは、グラフのタイプ`T`に応じて、$Graphs.jl$からの次数の定義が適用されます。異なる次数の定義を使用したい場合は、次数のベクトルをキーワード引数（`d⊥`、`d⊤`）として渡すことができます。基盤となるグラフなしで次数の列から直接モデルを生成したい場合は、単に次数の列を引数（`d⊥`、`d⊤`）として渡すことができます。隣接行列やエッジリストから作業したい場合は、$JuliaGraphs$エコシステムのグラフコンストラクタを使用できます。

次数がゼロのノードは他のノードに接続される確率がゼロであるため、モデルの計算ではスキップされます。

# 例

```jldoctest
# グラフからモデルを生成する
julia> G = corporateclub();

julia> model =  BiCM(G)
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (25 + 15 vertices, 6 + 6 unique degrees, 0.30 compression ratio)

```

```jldoctest
# 次数列から直接モデルを生成する
julia> model = model = BiCM(d⊥=[1,1,2,2,2,3,3,1,1,2], d⊤=[3,4,5,2,5,6,6,1,1,2])
BiCM{Nothing, Float64} (10 + 10 vertices, 3 + 6 unique degrees, 0.45 compression ratio)

```

```jldoctest
# 異なる精度で次数列から直接モデルを生成する
julia> model = model = BiCM(d⊥=[1,1,2,2,2,3,3,1,1,2], d⊤=[3,4,5,2,5,6,6,1,1,2], precision=Float32)
BiCM{Nothing, Float32} (10 + 10 vertices, 3 + 6 unique degrees, 0.45 compression ratio)

```

```jldoctest
# 隣接行列からモデルを生成する
julia> A = [0 0 0 1 0;0 0 0 1 0;0 0 0 0 1;1 1 0 0 0;0 0 1 0 0];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(A);

julia> @assert MaxEntropyGraphs.Graphs.is_bipartite(G); # グラフが二部グラフであるか確認

julia> model = BiCM(G) # モデルを生成する
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```

```jldoctest
# 二重隣接行列からモデルを生成する
julia> biadjacency = [1 0;1 0; 0 1];

julia> N⊥,N⊤ = size(biadjacency); # レイヤーの次元

julia> adjacency = [zeros(Int, N⊥,N⊥) biadjacency; biadjacency' zeros(Int,N⊤,N⊤)];

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(adjacency); # グラフを生成

julia> model = BiCM(G) # モデルを生成
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```

```jldoctest
# エッジリストからモデルを生成する
julia> edges = MaxEntropyGraphs.Graphs.SimpleEdge.([(1,4); (2,4); (3,5)]);

julia> G = MaxEntropyGraphs.Graphs.SimpleGraph(edges); # グラフを生成

julia> model = BiCM(G) # モデルを生成
BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (3 + 2 vertices, 1 + 2 unique degrees, 0.60 compression ratio)

```
