```
deflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

Return a polynomial with the same coefficients as $f$ but whose exponents have been deflated (divided) by the given exponents (supplied as an array of deflation factors, one for each variable).

The algorithm automatically replaces a deflation of $0$ by $1$, to avoid division by $0$.
