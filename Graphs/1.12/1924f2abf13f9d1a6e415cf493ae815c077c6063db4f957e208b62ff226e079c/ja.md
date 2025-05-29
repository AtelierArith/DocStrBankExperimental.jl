```
vertices(g)
```

グラフの頂点の（イテレータまたはコレクションとしての）返却。

### 実装ノート

返されたイテレータは頂点を一度だけ通過するのに有効であり、`g`への変更によって無効になります。

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
