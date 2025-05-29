```
abelian_group(E::EllipticCurve{<:FinFieldElem}) -> FinGenAbGroup, Map
```

Return an abelian group $A$ isomorphic to the group of rational points of $E$ and a map $E \to A$.

!!! warning
    The map is not implemented yet.


```jldoctest
julia> E = elliptic_curve(GF(101, 2), [1, 2]);

julia> A, _ = abelian_group(E);

julia> A
Z/2 x Z/5200
```
