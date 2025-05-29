```
findfirstrange(predicate, A::AbstractArray)
```

`predicate` が `true` を返す最初の連続したインデックス範囲を返します。そのような範囲がない場合は `nothing` を返します。

# 例

```jldoctest
julia> findfirstrange(isone, [2, 3, 1, 1, 1, 4, 1])
3:5

julia> findfirstrange(isone, [2, 3, 4, 1])
4:4

julia> findfirstrange(signbit, -5:5)
1:5
```
