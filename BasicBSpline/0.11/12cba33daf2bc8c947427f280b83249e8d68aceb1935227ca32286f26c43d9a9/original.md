Return dimention of a B-spline space.

$$
\dim(\mathcal{P}[p,k])
=\# k - p -1
$$

# Examples

```jldoctest
julia> dim(BSplineSpace{1}(KnotVector([1,2,3,4,5,6,7])))
5

julia> dim(BSplineSpace{1}(KnotVector([1,2,4,4,4,6,7])))
5

julia> dim(BSplineSpace{1}(KnotVector([1,2,3,5,5,5,7])))
5
```
