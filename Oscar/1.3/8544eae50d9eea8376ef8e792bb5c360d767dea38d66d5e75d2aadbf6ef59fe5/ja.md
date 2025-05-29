```
is_finite(G::GAPGroup) -> Bool
```

`G` が有限であれば `true` を返し、そうでなければ `false` を返します。

# 例

```jldoctest
julia> is_finite(symmetric_group(5))
true

julia> is_finite(free_group(2))
false

```
