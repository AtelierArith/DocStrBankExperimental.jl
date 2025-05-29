```
setindex(collection, v, i::Int)
```

インデックス `i` の値を `v` に設定した `collection` のコピーを返します。

# 例

```jldoctest
julia> x = StackVector([true, false])
2-element StackVector{2}:
 1
 0

julia> setindex(x, false, 1)
2-element StackVector{2}:
 0
 0
```
