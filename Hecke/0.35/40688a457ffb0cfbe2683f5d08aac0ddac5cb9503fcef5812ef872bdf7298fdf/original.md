```
gens(E::EllipticCurve{<:FinFieldElem}) -> Vector{EllipticCurvePoint}
```

Return a list of generators of the group of rational points on $E$.

# Examples

```jldoctest; filter = r"\(.*"
julia> E = elliptic_curve(GF(101, 2), [1, 2]);

julia> gens(E)
2-element Vector{EllipticCurvePoint{FqFieldElem}}:
 (13*o + 83 : 90*o + 25 : 1)
 (61*o + 62 : 19*o + 24 : 1)

julia> E = elliptic_curve(GF(101), [1, 2]);

julia> gens(E)
1-element Vector{EllipticCurvePoint{FqFieldElem}}:
 (27 : 57 : 1)
```
