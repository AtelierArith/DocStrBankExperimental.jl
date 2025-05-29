```
num_terms(f::Polynomial{F}) where F <: AbstractGaloisField -> Int
```

Return the number of non-zero terms (coefficients) in the polynomial `f`.

# Arguments

  * `f::Polynomial{F}`: The input polynomial.

# Returns

  * `Int`: The number of non-zero coefficients.

# Examples

julia> p = Polynomial([F2(1), F2(1), F2(0), F2(1)]); # 1 + x + x^3

julia> num_terms(p) 3
