```
is_directed(G)
```

グラフタイプ `G` が有向グラフであれば `true` を返し、それ以外の場合は `false` を返します。新しいグラフタイプは `is_directed(::Type{<:G})` を実装する必要があります。このメソッドは `is_directed(g::G)` でも呼び出すことができます。

# 例

```jldoctest
julia> using Graphs

julia> is_directed(SimpleGraph(2))
false

julia> is_directed(SimpleGraph)
false

julia> is_directed(SimpleDiGraph(2))
true
```
