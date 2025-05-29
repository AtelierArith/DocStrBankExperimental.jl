```
polynomial_from_roots(r::AbstractVector{T}, var::Polynomials.SymbolLike=:x)::Polynomial{T} where {T}
```

Generate a polynomial from its roots.

# Arguments

  * `r`: An array of roots
  * `var`: The variable symbol for the polynomial (default: :x)

# Returns

  * `Polynomial{T}`: The polynomial with the given roots

# Examples

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> roots = [α, α^2]
julia> polynomial_from_roots(roots)
Polynomial(1 + x + x^2)
```
