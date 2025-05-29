```
vertices(g)
```

グラフの頂点（イテレータまたはコレクション）を返します。

### 実装ノート

返されたイテレータはエッジを一度だけ通過するのに有効であり、`g`への変更によって無効になります。

# 例

```jldoctest
julia> using LightGraphs

julia> collect(vertices(SimpleGraph(4)))
4-element Array{Int64,1}:
 1
 2
 3
 4
```
