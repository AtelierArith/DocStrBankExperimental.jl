```
has_edge(g, s, d)
```

グラフ `g` がノード `s` からノード `d` へのエッジを持っている場合は true を返します。

オプションの `has_edge(g, e)` を実装して、ソースおよび宛先ノード以外のデータを含むエッジがグラフに属しているかどうかを確認できます。

`e ∈ edges(g)` または `e ∈ edges(g)` は `has_edge` への呼び出しとして評価されます。参照: [`edges`](@ref)。

# 例

```jldoctest
julia> using LightGraphs

julia> g = SimpleDiGraph(2);

julia> add_edge!(g, 1, 2);

julia> has_edge(g, 1, 2)
true

julia> has_edge(g, 2, 1)
false
```
