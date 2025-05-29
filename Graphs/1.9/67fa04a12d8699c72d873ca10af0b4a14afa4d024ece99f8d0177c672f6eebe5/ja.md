```
add_vertices!(g, n)
```

グラフ `g` に `n` 個の新しい頂点を追加します。成功裏に追加された頂点の数を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph()
{0, 0} 無向単純 Int64 グラフ

julia> add_vertices!(g, 2)
2
```
