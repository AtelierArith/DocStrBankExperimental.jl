```
intervalindex(vec, x[, start])
```

If `v` is an `AbstractVector`, return the largest index `i` so that `vec[i] ≤ x ≤ vec[end]` and `vec[i] < vec[end]`. Return `nothing` if no such index exists. The vector `vec` is assumed to be sorted in ascending order.

If `vec` is a [`BSplineBasis`](@ref), return `intervalindex(knots(vec), x[, start])`.

If `start` is given, a linear search is performed, starting from the index `start` going forward or backward. If `start` is not given, a binary search is performed.

# Examples

```jldoctest
julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 2.5)
3

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 7) # returns nothing

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 1)
2

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 4)
7

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 6.0)
8
```
