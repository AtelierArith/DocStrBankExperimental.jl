```
unbounded_mapping(M::BSplineManifold{Dim}, t::Vararg{Real,Dim})
```

# 例

```jldoctest
julia> P = BSplineSpace{1}(KnotVector([0,0,1,1]))
BSplineSpace{1, Int64, KnotVector{Int64}}(KnotVector([0, 0, 1, 1]))

julia> domain(P)
0 .. 1

julia> M = BSplineManifold([0,1], P);


julia> unbounded_mapping(M, 0.1)
0.1

julia> M(0.1)
0.1

julia> unbounded_mapping(M, 1.2)
1.2

julia> M(1.2)
ERROR: DomainError with 1.2:
The input 1.2 is out of domain 0 .. 1.
[...]
```
