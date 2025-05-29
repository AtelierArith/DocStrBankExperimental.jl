```
abelian_group(E::EllipticCurve{<:FinFieldElem}) -> FinGenAbGroup, Map
```

有理点の群 $E$ に同型なアーベル群 $A$ と、写像 $E \to A$ を返します。

!!! warning
    この写像はまだ実装されていません。


```jldoctest
julia> E = elliptic_curve(GF(101, 2), [1, 2]);

julia> A, _ = abelian_group(E);

julia> A
Z/2 x Z/5200
```
