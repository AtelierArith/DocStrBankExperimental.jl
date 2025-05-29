```
anyone(index::Integer, mask::Integer) -> Bool
```

マスクされたインデックスの位置に1がある場合は`true`を返します。

# 例

マスクされた位置に1がある場合は`true`です。

```jldoctest
julia> anyone(0b1011, 0b1001)
true

julia> anyone(0b1011, 0b1100)
true

julia> anyone(0b1011, 0b0100)
false
```
