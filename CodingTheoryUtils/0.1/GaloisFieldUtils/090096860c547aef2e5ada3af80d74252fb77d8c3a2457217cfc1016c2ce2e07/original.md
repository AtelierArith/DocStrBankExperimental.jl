```
extract_degrees(polynomial::AbstractString) -> Vector{Int}
```

Extract the degrees of the terms in a polynomial string representation.

The polynomial string should be in the format "x^a + x^b + ... + 1". Terms should be separated by " + ".

# Examples

julia> extract_degrees("x^3 + x + 1") 3-element Vector{Int64}:  3  1  0

julia> extract_degrees("x^5") 1-element Vector{Int64}:  5
