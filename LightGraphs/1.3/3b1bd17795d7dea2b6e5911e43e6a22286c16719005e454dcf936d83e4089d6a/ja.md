```
maximal_cliques(g)
```

無向グラフ `g` に見つかった各最大クリークのノードインデックスを表すベクトルのベクトルを返します。

```jldoctest
julia> using LightGraphs
julia> g = SimpleGraph(3)
julia> add_edge!(g, 1, 2)
julia> add_edge!(g, 2, 3)
julia> maximal_cliques(g)
2-element Array{Array{Int64,N},1}:
 [2,3]
 [2,1]
```
