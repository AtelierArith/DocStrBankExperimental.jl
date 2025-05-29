```
deleteat(vec::StaticVector, index::Integer)
```

指定された `index` のアイテムが削除された新しいベクターを返します。

# 例

```jldoctest
julia> deleteat(@SVector[6, 5, 4, 3, 2, 1], 2)
5-element SVector{5, Int64} with indices SOneTo(5):
 6
 4
 3
 2
 1
```
