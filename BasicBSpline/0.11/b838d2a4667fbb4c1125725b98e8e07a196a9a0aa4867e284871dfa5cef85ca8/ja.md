Bスプライン空間を与えられた追加の次数とノットベクトルで拡張します。この関数は `issqsubset` (`⊑`) と互換性があります。

# 例

```jldoctest
julia> k = KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0]);


julia> P = BSplineSpace{2}(k);


julia> P′ = expandspace_I(P, Val(1), KnotVector([6.0]))
BSplineSpace{3, Float64, KnotVector{Float64}}(KnotVector([0.0, 1.5, 2.5, 2.5, 5.5, 5.5, 6.0, 8.0, 8.0, 9.0, 9.0, 9.5, 10.0]))

julia> P ⊆ P′
false

julia> P ⊑ P′
true

julia> domain(P)
2.5 .. 9.0

julia> domain(P′)
2.5 .. 9.0
```
