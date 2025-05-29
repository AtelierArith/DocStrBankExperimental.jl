```
monomials(x::AbstractVector{String}, d::Integer, mo::MonomialOrder; include_zero::Bool=false)
```

Computes all monomials of the variables `x` up to degree `d` ordered in monomial order `mo`.

Pass `include_zero=true` to include the zero degree monomial.

# Examples

```julia-repl
julia> monomials(["x","y"], 2, LexicographicOrder(); include_zero=true)
5-element Vector{Monomial}:
1
y
 y²
 x
 xy
 x²
```
