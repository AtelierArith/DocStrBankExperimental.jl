```
findfirstrange(predicate, A::AbstractArray)
```

Return the first consecutive index range for which the `predicate` returns `true`. Return `nothing` if there is no such range.

# Examples

```jldoctest
julia> findfirstrange(isone, [2, 3, 1, 1, 1, 4, 1])
3:5

julia> findfirstrange(isone, [2, 3, 4, 1])
4:4

julia> findfirstrange(signbit, -5:5)
1:5
```
