```
variable(var=:x)
variable(::Type{<:AbstractPolynomial}, var=:x)
variable(p::AbstractPolynomial, var=indeterminate(p))
```

Return the monomial `x` in the indicated polynomial basis.  If no type is give, will default to [`Polynomial`](@ref). Equivalent to `P(var)`.

# Examples

```jldoctest
julia> using Polynomials

julia> x = variable()
Polynomial(x)

julia> p = 100 + 24x - 3x^2
Polynomial(100 + 24*x - 3*x^2)

julia> roots((x - 3) * (x + 2))
2-element Vector{Float64}:
 -2.0
  3.0
```
