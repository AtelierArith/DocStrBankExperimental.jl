```
string2F2poly(polynomial::AbstractString) -> Polynomial{F2, :x}
```

Convert a polynomial string representation into a Polynomial{F2, :x} object.

# Examples

julia> string2F2poly("x^3 + x + 1") Polynomial(1 + x + x^3)

julia> string2F2poly("x^5") Polynomial(x^5)
