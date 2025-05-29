Return the support of $i$-th B-spline basis function.

$$
\operatorname{supp}(B_{(i,p,k)})=[k_{i},k_{i+p+1}]
$$

# Examples

```jldoctest
julia> k = KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0])
KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0])

julia> P = BSplineSpace{2}(k)
BSplineSpace{2, Float64, KnotVector{Float64}}(KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0]))

julia> bsplinesupport_R(P,1)
0.0 .. 5.5

julia> bsplinesupport_R(P,2)
1.5 .. 8.0
```
