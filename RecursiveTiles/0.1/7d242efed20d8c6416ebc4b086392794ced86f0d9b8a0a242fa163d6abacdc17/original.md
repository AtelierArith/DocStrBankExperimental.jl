```
findlastrange(predicate, A::AbstractArray)
```

Return the last consecutive index range for which the `predicate` returns `true`. Return `nothing` if there is no such range.

# Examples

```jldoctest
julia> findlastrange(isone, [2, 3, 1, 1, 1, 4, 1])
7:7

julia> findlastrange(isone, [2, 3, 4, 1])
4:4

julia> findlastrange(signbit, -5:5)
1:5
```
