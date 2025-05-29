```
is_weakly_connected(g)
```

グラフ `g` が弱連結であれば `true` を返します。もし `g` が無向グラフであれば、この関数は [`is_connected(g)`](@ref) と同等です。

# 例

```jldoctest
julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> is_weakly_connected(g)
true

julia> g = SimpleDiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> is_connected(g)
true

julia> is_strongly_connected(g)
false

julia> is_weakly_connected(g)
true
```
