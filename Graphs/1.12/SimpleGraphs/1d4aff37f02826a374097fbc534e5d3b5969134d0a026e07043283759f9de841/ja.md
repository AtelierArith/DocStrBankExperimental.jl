```
SimpleGraphFromIterator(iter)
```

イテレータ `iter` から [`SimpleGraph`](@ref) を作成します。iter の要素は `type <: SimpleEdge` でなければなりません。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> h = SimpleGraphFromIterator(edges(g));

julia> collect(edges(h))
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 2 => 3
```
