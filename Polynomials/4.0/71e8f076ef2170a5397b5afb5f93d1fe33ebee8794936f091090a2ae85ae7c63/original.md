```
mapdomain(::Type{<:AbstractPolynomial}, x::AbstractArray)
mapdomain(::AbstractPolynomial, x::AbstractArray)
```

Given values of x that are assumed to be unbounded (-∞, ∞), return values rescaled to the domain of the given polynomial.

# Examples

```jldoctest
julia> using Polynomials

julia> x = -10:10
-10:10

julia> extrema(mapdomain(ChebyshevT, x))
(-1.0, 1.0)

```
