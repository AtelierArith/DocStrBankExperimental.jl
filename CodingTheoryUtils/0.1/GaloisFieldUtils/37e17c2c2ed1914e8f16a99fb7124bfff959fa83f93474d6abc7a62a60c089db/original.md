```
string2coefvec(polynomial::AbstractString) -> Vector{Int}
```

Convert a polynomial string representation into a coefficient vector (Int). Assumes the polynomial is over GF(2), so coefficients are 0 or 1. The vector index corresponds to the degree (index 1 is degree 0).

# Examples

julia> string2coefvec("x^3 + x + 1") 4-element Vector{Int64}:  1  1  0  1

julia> string2coefvec("x^5") 6-element Vector{Int64}:  0  0  0  0  0  1
