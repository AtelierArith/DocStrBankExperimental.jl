```
findlastrange(predicate, A::AbstractArray)
```

`predicate` が `true` を返す最後の連続したインデックス範囲を返します。そのような範囲がない場合は `nothing` を返します。

# 例

```jldoctest
julia> findlastrange(isone, [2, 3, 1, 1, 1, 4, 1])
7:7

julia> findlastrange(isone, [2, 3, 4, 1])
4:4

julia> findlastrange(signbit, -5:5)
1:5
```
