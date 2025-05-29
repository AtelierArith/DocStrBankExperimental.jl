```
fromroots(::AbstractVector{<:Number}; var=:x)
fromroots(::Type{<:AbstractPolynomial}, ::AbstractVector{<:Number}; var=:x)
```

Construct a polynomial of the given type given the roots. If no type is given, defaults to `Polynomial`.

# Examples

```jldoctest
julia> using Polynomials

julia> r = [3, 2]; # (x - 3)(x - 2)

julia> fromroots(r)
Polynomial(6 - 5*x + x^2)
```
