```
is_subset(H::GAPGroup, G::GAPGroup)
```

`H`が`G`の部分集合であれば`true`を返し、そうでなければ`false`を返します。

# 例

```jldoctest
julia> g = symmetric_group(300); h = derived_subgroup(g)[1];

julia> is_subset(h, g)
true

julia> is_subset(g, h)
false
```
