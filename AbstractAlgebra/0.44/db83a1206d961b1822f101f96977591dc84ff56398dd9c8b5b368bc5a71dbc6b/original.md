```
inflate(f::MPolyRingElem, vars::Vector{Int}, shift::Vector{Int}, defl::Vector{Int})
```

Return a polynomial with the same coefficients as $f$ but where exponents of some variables (supplied as an array of variable indices) have been inflated (multiplied) by the given deflation exponents (supplied as an array of inflation factors) and then increased by the given shifts (again supplied as an array of shifts).
