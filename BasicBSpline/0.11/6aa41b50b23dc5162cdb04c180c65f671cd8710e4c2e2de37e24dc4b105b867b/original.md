Expand B-spline space with given additional degree and knotvector. This function is compatible with `issubset` (`⊆`).

# Examples

```jldoctest
julia> k = KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0]);


julia> P = BSplineSpace{2}(k);


julia> P′ = expandspace_R(P, Val(1), KnotVector([6.0]))
BSplineSpace{3, Float64, KnotVector{Float64}}(KnotVector([0.0, 0.0, 1.5, 1.5, 2.5, 2.5, 5.5, 5.5, 6.0, 8.0, 8.0, 9.0, 9.0, 9.5, 9.5, 10.0, 10.0]))

julia> P ⊆ P′
true

julia> P ⊑ P′
false

julia> domain(P)
2.5 .. 9.0

julia> domain(P′)
1.5 .. 9.5
```
