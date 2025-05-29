Gegenbauer{α, T <: Number}

The Gegenbauer polynomials have weight function `(1-x^2)^(α-1/2)` over the domain `[-1,1]`. The parameter `α` is specified in the constructor. These are also called the ultra-spherical polynomials. The Legendre polynomials are the specialization  `Gegenbauer{1/2}`.

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p =  Gegenbauer{1/2}([1,2,3])
Gegenbauer{0.5}(1⋅Cᵅ₀(x) + 2⋅Cᵅ₁(x) + 3⋅Cᵅ₂(x))

julia> convert(Polynomial, p)
Polynomial(-0.5 + 2.0*x + 4.5*x^2)
```
