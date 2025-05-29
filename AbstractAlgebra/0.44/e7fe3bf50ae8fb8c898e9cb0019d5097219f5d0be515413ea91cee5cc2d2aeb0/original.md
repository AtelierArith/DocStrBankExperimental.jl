```
deflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

Return a polynomial with the same coefficients as $f$ but whose exponents have been deflated maximally, i.e. with each exponent divide by the largest integer which divides the degrees of all exponents of that variable in $f$.
