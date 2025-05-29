```
pop(vec::StaticVector)
```

`vec`の最後のアイテムを削除した新しいベクターを返します。

# 例

```jldoctest
julia> pop(@SVector[1,2,3])
2-element SVector{2, Int64} with indices SOneTo(2):
 1
 2
```
