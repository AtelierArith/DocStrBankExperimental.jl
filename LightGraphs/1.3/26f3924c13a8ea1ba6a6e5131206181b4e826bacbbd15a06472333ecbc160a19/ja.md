```
edges(g)
```

グラフのエッジ（辺）のイテレータまたはコレクションを返します。`AbstractSimpleGraph`の場合、`SimpleEdgeIter`を返します。`e in edges(g)`および`e ∈ edges(ga)`の式は、[`has_edge`](@ref)への呼び出しとして評価されます。

### 実装ノート

返されたイテレータはエッジを一度だけ通過するのに有効であり、`g`への変更によって無効になります。

# 例

```jldoctest
julia> using LightGraphs

julia> g = path_graph(3);

julia> collect(edges(g))
2-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
```
