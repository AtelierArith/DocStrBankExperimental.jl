```
is_connected(g)
```

グラフ `g` が連結であれば `true` を返します。有向グラフの場合、グラフ `g` が弱連結であれば `true` を返します。

# 例

```jldoctest
julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> is_connected(g)
true

julia> g = SimpleGraph([0 1 0 0 0; 1 0 1 0 0; 0 1 0 0 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> is_connected(g)
false

julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_connected(g)
true
```
