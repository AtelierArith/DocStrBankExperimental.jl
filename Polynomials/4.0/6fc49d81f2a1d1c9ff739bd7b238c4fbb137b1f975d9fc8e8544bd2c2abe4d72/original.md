```
fromroots(::AbstractMatrix{<:Number}; var=:x)
fromroots(::Type{<:AbstractPolynomial}, ::AbstractMatrix{<:Number}; var=:x)
```

Construct a polynomial of the given type using the eigenvalues of the given matrix as the roots. If no type is given, defaults to `Polynomial`.

# Examples

```jldoctest
julia> using Polynomials

julia> A = [1 2; 3 4]; # (x - 5.37228)(x + 0.37228)

julia> fromroots(A)
Polynomial(-1.9999999999999998 - 5.0*x + 1.0*x^2)
```
