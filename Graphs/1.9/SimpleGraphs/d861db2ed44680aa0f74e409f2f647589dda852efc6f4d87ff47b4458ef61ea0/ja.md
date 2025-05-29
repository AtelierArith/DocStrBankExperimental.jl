```
add_edge!(g, e)
```

グラフ `g` にエッジ `e` を追加します。エッジが正常に追加された場合は `true` を返し、そうでない場合は `false` を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(2);

julia> add_edge!(g, 1, 2)
true

julia> add_edge!(g, 2, 3)
false
```
