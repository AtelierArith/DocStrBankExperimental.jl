```
polynomial_to_power_sums(f::PolyRingElem{T}, n::Int=degree(f)) where T <: RingElement -> Vector{T}
```

Uses Newton (or Newton-Girard) formulas to compute the first $n$ sums of powers of the roots of $f$ from the coefficients of $f$, starting with the sum of (first powers of) the roots. The input polynomial must be monic, at least degree $1$ and have nonzero constant coefficient.
