```
inflate(f::T, vars::Vector{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: MPolyRingElem
```

Return a polynomial with the same coefficients as $f$ but where the exponents of the given variables have been inflated (multiplied) by the given deflation exponents (supplied as an array of inflation factors) and then increased by the given shifts (again supplied as an array of shifts).
