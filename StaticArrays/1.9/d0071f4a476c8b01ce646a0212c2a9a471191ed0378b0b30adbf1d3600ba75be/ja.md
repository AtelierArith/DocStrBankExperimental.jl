```
pushfirst(vec::StaticVector, item)
```

`vec`の先頭に`item`を挿入した新しい`StaticVector`を返します。

# 例

```jldoctest
julia> pushfirst(@SVector[1, 2, 3, 4], 5)
5-element SVector{5, Int64} with indices SOneTo(5):
 5
 1
 2
 3
 4
```
