```
function print_stevens_expansion(op)
```

Prints a local Hermitian operator as a linear combination of Stevens operators. The operator `op` may be a finite-dimensional matrix or an abstract spin polynomial in the large-$s$ limit.

# Examples

```julia
S = spin_matrices(2)
print_stevens_expansion(S[1]^4 + S[2]^4 + S[3]^4)
# Prints: (1/20)𝒪₄₀ + (1/4)𝒪₄₄ + 102/5

S = spin_matrices(Inf)
print_stevens_expansion(S[1]^4 + S[2]^4 + S[3]^4)
# Prints: (1/20)𝒪₄₀ + (1/4)𝒪₄₄ + (3/5)𝒮⁴
```
