```
allone(index::Integer, mask::Integer) -> Bool
```

インデックスのすべてのマスクされた位置が1であれば`true`を返します。

# 例

すべてのマスクされた位置が1であれば`true`。

```jldoctest
julia> allone(0b1011, 0b1011)
true

julia> allone(0b1011, 0b1001)
true

julia> allone(0b1011, 0b0100)
false
```
