```
is_strongly_connected(g)
```

有向グラフ `g` が強連結であれば `true` を返します。

# 例

```jldoctest
julia> g = DiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_strongly_connected(g)
true
```
