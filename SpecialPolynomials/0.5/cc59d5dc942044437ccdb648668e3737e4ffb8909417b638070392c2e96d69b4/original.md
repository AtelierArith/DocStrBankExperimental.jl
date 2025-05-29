```
Jacobi{α,  β, T}
```

Implements the [Jacobi](https://en.wikipedia.org/wiki/Jacobi_polynomials) polynomials. These have weight function `w(x) = (1-x)^α ⋅ (1+x)^β` over the domain `[-1,1]`. Many orthogonal polynomial types are special cases. The parameters are  specified to the constructors:

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = Jacobi{-1/2, -1/2}([0,0,1])
Jacobi{-0.5,-0.5}(1⋅Jᵅᵝ₂(x))

julia> convert(Polynomial, p)
Polynomial(-0.375 + 0.75*x^2)

julia> monic(p) = (q=convert(Polynomial,p); q/q[end])
monic (generic function with 1 method)

julia> monic(p) ≈  monic(basis(Chebyshev, 2))
true

```

Special cases include `Jacobi{α-1/2,α-1/2} = Gegenbauer{α}`, `Jacobi{-1/2,-1/2} = Chebyshev`, `Jacobi{1/2,1/2} = ChebyshevU`, and `Jacobi{0,0} = Legendre`.
