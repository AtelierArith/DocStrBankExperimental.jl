```
SimpleDiGraph(g::AbstractSimpleGraph)
```

グラフ `g` から有向 `SimpleDiGraph` を構築します。要素の型は `g` と同じです。

## 例

```jldoctest
julia> g = path_graph(Int8(5))
julia> SimpleDiGraph(g)
{5, 8} 有向単純 Int8 グラフ
```
