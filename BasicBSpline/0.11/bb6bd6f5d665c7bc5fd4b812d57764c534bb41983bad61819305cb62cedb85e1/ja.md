与えられた制御点とBスプライン空間からBスプライン多様体を構築します。

# 例

```jldoctest
julia> using StaticArrays

julia> P = BSplineSpace{2}(KnotVector([0,0,0,1,1,1]))
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([0, 0, 0, 1, 1, 1]))

julia> a = [SVector(1,0), SVector(1,1), SVector(0,1)]
3-element Vector{SVector{2, Int64}}:
 [1, 0]
 [1, 1]
 [0, 1]

julia> M = BSplineManifold(a, P);


julia> M(0.4)
2-element SVector{2, Float64} with indices SOneTo(2):
 0.84
 0.64

julia> M(1.2)
ERROR: DomainError with 1.2:
The input 1.2 is out of domain 0 .. 1.
[...]
```
