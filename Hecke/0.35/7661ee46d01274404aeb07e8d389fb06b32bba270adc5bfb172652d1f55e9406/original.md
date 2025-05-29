```
order(E::EllipticCurve{<: FinFieldElem}) -> ZZRingElem
```

Given an elliptic curve $E$ over a finite field $\mathbf F$, compute $\#E(\mathbf F)$.

# Examples

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> order(E)
100
```
