```
insert(vec::StaticVector, index::Integer, item)
```

指定された `index` に `item` を挿入した新しいベクターを返します。

# 例

```jldoctest
julia> insert(@SVector[6, 5, 4, 2, 1], 4, 3)
6-element SVector{6, Int64} with indices SOneTo(6):
 6
 5
 4
 3
 2
 1
```
