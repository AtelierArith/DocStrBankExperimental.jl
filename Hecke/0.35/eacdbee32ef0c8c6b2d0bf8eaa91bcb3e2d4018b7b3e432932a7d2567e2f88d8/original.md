```
trace_of_frobenius(E::EllipticCurve{<: FinFieldElem}, r::Int) -> ZZRingElem
```

Return the trace of the $r$-th power of the Frobenius endomorphism on the elliptic curve $E$.

```jldoctest
julia> E = elliptic_curve(GF(101, 2), [1, 2]);

julia> trace_of_frobenius(E, 2)
18802
```
