B-spline basis functions at point `t` on `i`-th interval.

# Examples

```jldoctest
julia> k = KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0])
KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0])

julia> p = 2
2

julia> P = BSplineSpace{p}(k)
BSplineSpace{2, Float64, KnotVector{Float64}}(KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0]))

julia> t = 5.7
5.7

julia> i = intervalindex(P,t)
2

julia> bsplinebasisall(P,i,t)
3-element SVector{3, Float64} with indices SOneTo(3):
 0.3847272727272727
 0.6107012987012989
 0.00457142857142858

julia> bsplinebasis.(P,i:i+p,t)
3-element Vector{Float64}:
 0.38472727272727264
 0.6107012987012989
 0.00457142857142858
```
