```
add_vertex!(g)
```

グラフ `g` に新しい頂点を追加します。追加が成功した場合は `true` を返します。

# 例

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(Int8(typemax(Int8) - 1))
{126, 0} 無向単純 Int8 グラフ

julia> add_vertex!(g)
true

julia> add_vertex!(g)
false
```
