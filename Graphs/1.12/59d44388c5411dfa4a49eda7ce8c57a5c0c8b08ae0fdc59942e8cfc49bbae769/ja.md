```
maximal_cliques(g)
```

無向グラフ `g` に見つかった各最大クリークのノードインデックスを表すベクトルのベクトルを返します。

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3)
{3, 0} undirected simple Int64 graph

julia> add_edge!(g, 1, 2)
true

julia> add_edge!(g, 2, 3)
true

julia> maximal_cliques(g)
2-element Vector{Vector{Int64}}:
 [2, 3]
 [2, 1]
```
