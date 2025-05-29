```
deflate(f::MPolyRingElem, vars::Vector{Int}, shift::Vector{Int}, defl::Vector{Int})
```

Return a polynomial with the same coefficients as $f$ but where exponents of some variables (supplied as an array of variable indices) have been reduced by the given shifts (supplied as an array of shifts), then deflated (divided) by the given exponents (again supplied as an array of deflation factors). The algorithm automatically replaces a deflation of $0$ by $1$, to avoid division by $0$.
