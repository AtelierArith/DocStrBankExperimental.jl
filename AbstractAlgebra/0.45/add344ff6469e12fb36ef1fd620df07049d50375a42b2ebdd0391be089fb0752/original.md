```
deflate(f::T, vars::Vector{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: MPolyRingElem
```

Return a polynomial with the same coefficients as $f$ but where the exponents of the given variables have been reduced by the given shifts (supplied as an array of shifts), then deflated (divided) by the given exponents (again supplied as an array of deflation factors). The algorithm automatically replaces a deflation of $0$ by $1$, to avoid division by $0$.
