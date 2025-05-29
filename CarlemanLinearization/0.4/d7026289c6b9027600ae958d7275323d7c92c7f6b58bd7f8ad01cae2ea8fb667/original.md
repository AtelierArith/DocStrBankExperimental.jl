```
kron_pow(x::Vector{<:AbstractVariable}, pow::Int)
```

Compute the higher order concrete Kronecker power: `x ⊗ x ⊗ ... ⊗ x`, `pow` times for a vector of symbolic monomials.

### Input

  * `x`   – polynomial variable
  * `pow` – integer

### Output

Vector of multivariate monomial corresponding to `x^{⊗ pow}`.

### Examples

```jldoctest
julia> using DynamicPolynomials

julia> @polyvar x[1:2]
(PolyVar{true}[x₁, x₂],)

julia> x
2-element Vector{PolyVar{true}}:
 x₁
 x₂

julia> kron_pow(x, 2)
4-element Vector{Monomial{true}}:
 x₁²
 x₁x₂
 x₁x₂
 x₂²
```
