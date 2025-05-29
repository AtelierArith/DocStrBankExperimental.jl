```
inflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

Return a polynomial with the same coefficients as $f$ but whose exponents have been inflated (multiplied) by the given deflation exponents (supplied as an array of inflation factors, one for each variable).
