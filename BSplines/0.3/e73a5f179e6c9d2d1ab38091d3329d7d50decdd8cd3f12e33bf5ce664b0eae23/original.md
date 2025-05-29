```
intervalindices(basis::BSplineBasis, indices=eachindex(basis))
```

Return an iterator that yields the indices of all intervals on which `basis` is defined, i.e., it produces all indices `ind` (in ascending order) for which `(knots(basis)[ind], knots(basis)[ind+1])` is such an interval. 

If a range of `indices` is supplied, the iterator yields only those intervals on which *at least one* of the B-splines `basis[j] for j=indices` is non-zero.

# Examples

```jldoctest
julia> intervalindices(BSplineBasis(3, 0:5))
3:7

julia> intervalindices(BSplineBasis(3, 0:5), 1:4)
3:6

julia> intervalindices(BSplineBasis(4, [1,2,3,4,4,4,5,6]))
BSplines.IntervalIndices{Vector{Int64}}([1, 2, 3, 4, 4, 4, 5, 6], 1:8, 3)

julia> collect(ans)
5-element Vector{Int64}:
  4
  5
  6
  9
 10
```
