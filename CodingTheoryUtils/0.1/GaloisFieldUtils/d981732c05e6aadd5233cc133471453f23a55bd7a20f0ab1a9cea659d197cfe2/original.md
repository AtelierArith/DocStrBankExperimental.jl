```
make_companion_matrix(g::Vector{F})::Matrix{F} where F <: GaloisFields.AbstractGaloisField
```

Generate a companion matrix from a polynomial's coefficient vector.

# Arguments

  * `g::Vector{F}`: Coefficient vector of the polynomial (excluding constant term)

# Returns

  * `Matrix{F}`: Companion matrix

# Examples

```julia
F2 = @GaloisField 2
g = [F2(1), F2(1)]  # Coefficients of x^2 + x + 1
A = make_companion_matrix(g)
```
