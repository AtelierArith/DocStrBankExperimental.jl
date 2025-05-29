Construct Rational B-spline manifold from given control points, weights and B-spline spaces.

# Examples

```jldoctest
julia> using StaticArrays, LinearAlgebra

julia> P = BSplineSpace{2}(KnotVector([0,0,0,1,1,1]))
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([0, 0, 0, 1, 1, 1]))

julia> w = [1, 1/√2, 1]
3-element Vector{Float64}:
 1.0
 0.7071067811865475
 1.0

julia> a = [SVector(1,0), SVector(1,1), SVector(0,1)]
3-element Vector{SVector{2, Int64}}:
 [1, 0]
 [1, 1]
 [0, 1]

julia> M = RationalBSplineManifold(a,w,P);  # 1/4 arc


julia> M(0.3)
2-element SVector{2, Float64} with indices SOneTo(2):
 0.8973756499953727
 0.4412674277525845

julia> norm(M(0.3))
1.0
```
