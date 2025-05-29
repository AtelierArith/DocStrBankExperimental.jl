```
vertices(g)
```

グラフの頂点（イテレータまたはコレクション）を返します。

### 実装ノート

返されたイテレータはエッジを一度だけ通過するのに有効であり、`g`への変更によって無効になります。

# 例

```jldoctest
julia> using Graphs

julia> collect(vertices(SimpleGraph(4)))
4-element Vector{Int64}:
 1
 2
 3
 4
```
