```
intervalindices(basis::BSplineBasis, i, j, ...)
```

For integers `i`, `j`, …, return an iterator that yields the indices of all intervals on which *all* of the B-splines `basis[i]`, `basis[j]`, … are non-zero, i.e., it produces all indices `ind` (in ascending order) for which `(knots(basis)[ind], knots(basis)[ind+1])` is such an interval.

# Examples

```jldoctest
julia> intervalindices(BSplineBasis(3, 0:5), 3)
3:5

julia> intervalindices(BSplineBasis(3, 0:5), 4, 5)
5:6

julia> intervalindices(BSplineBasis(3, 0:5), 2, 6) # B-splines do not overlap
6:5

julia> intervalindices(BSplineBasis(3, 0:5), 3, 5, 4)
5:5

julia> intervalindices(BSplineBasis(4, [1,2,3,4,4,4,5,6]), 3, 5)
BSplines.IntervalIndices{Vector{Int64}}([1, 2, 3, 4, 4, 4, 5, 6], 2:4, 3)

julia> collect(ans)
2-element Vector{Int64}:
 5
 6
```
