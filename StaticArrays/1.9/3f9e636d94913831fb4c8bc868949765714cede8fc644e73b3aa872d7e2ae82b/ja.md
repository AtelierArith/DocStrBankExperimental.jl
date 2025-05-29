```
push(vec::StaticVector, item)
```

`vec`の末尾に`item`を挿入した新しい`StaticVector`を返します。

# 例

```jldoctest
julia> push(@SVector[1, 2, 3], 4)
4-element SVector{4, Int64} with indices SOneTo(4):
 1
 2
 3
 4
```
