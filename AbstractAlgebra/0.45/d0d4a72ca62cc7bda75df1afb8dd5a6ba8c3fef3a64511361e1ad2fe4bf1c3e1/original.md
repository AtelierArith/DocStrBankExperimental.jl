```
deflate(f::MPolyRingElem{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: RingElement
```

Return a polynomial with the same coefficients as $f$ but whose exponents have been reduced by the given shifts (supplied as an array of shifts, one for each variable), then deflated (divided) by the given exponents (again supplied as an array of deflation factors, one for each variable). The algorithm automatically replaces a deflation of $0$ by $1$, to avoid division by $0$.
