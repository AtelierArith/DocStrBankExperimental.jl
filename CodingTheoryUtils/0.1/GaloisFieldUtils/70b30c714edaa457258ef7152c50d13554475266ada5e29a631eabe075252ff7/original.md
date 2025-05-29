```
gf_pretty(v::Vector{F2})::String
```

Pretty print a binary vector (F2) as a polynomial string (e.g., "1 + x^2"). Corresponds to the polynomial whose coefficients are the elements of `v`.

# Arguments

  * `v::Vector{F2}`: The binary vector.

# Returns

  * `String`: The polynomial string representation, or "0" for zero/empty vector.

# Examples

```julia
gf_pretty([F2(1), F2(0), F2(1)]) == "1 + x^2"
gf_pretty([F2(0), F2(1)]) == "x"
gf_pretty(F2[]) == "0"
```
