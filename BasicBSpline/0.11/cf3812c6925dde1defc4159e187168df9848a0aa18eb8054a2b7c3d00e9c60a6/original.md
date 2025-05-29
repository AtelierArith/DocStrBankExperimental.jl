Check if given B-spline space is non-degenerate.

# Examples

```jldoctest
julia> isnondegenerate(BSplineSpace{2}(KnotVector([1,3,5,6,8,9])))
true

julia> isnondegenerate(BSplineSpace{1}(KnotVector([1,3,3,3,8,9])))
false
```
