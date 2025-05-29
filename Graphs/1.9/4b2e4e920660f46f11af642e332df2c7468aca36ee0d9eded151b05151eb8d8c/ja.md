```
size(g, i)
```

`g`の頂点数を返します。`i`が1または2の場合は頂点数を、そうでない場合は`1`を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = cycle_graph(4);

julia> size(g, 1)
4

julia> size(g, 2)
4

julia> size(g, 3)
1
```
