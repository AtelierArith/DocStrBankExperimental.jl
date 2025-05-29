```
trace_of_frobenius(E::EllipticCurve{FinFieldElem}) -> Int
```

Return the trace of the Frobenius endomorphism on the elliptic curve $E$ over $\mathbf{F}_q$. This is equal to $q + 1 - n$ where n is the number of points on $E$ over $\mathbf{F}_q$.

# Examples

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> trace_of_frobenius(E) == 101 + 1 - order(E)
true
```
