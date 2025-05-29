```
power_sums_to_polynomial(P::Vector{T};
                 parent::PolyRing{T}=PolyRing(parent(P[1])) where T <: RingElement -> PolyRingElem{T}
```

Uses the Newton (or Newton-Girard) identities to obtain the polynomial with given sums of powers of roots. The list must be nonempty and contain `degree(f)` entries where $f$ is the polynomial to be recovered. The list must start with the sum of first powers of the roots.
