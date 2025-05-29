```
Legendre{T}
```

Implements the [Legendre](https://en.wikipedia.org/wiki/Legendre_polynomials) polynomials. These have weight function `w(x) = 1` over the domain `[-1,1]`.

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = Legendre([1,2,3])
Legendre(1⋅P₀(x) + 2⋅P₁(x) + 3⋅P₂(x))

julia> convert(Polynomial, p)
Polynomial(-0.5 + 2.0*x + 4.5*x^2)

julia> p2m, p2m1 = basis.(Legendre, (8,9)) # evaluation P_{2m+k}(-1) =  (-1)^k
(Legendre(1.0⋅P₈(x)), Legendre(1.0⋅P₉(x)))

julia> p2m(-1) == 1
false

julia> p2m1(-1) == -1
false

julia> n = 5  # verify  Rodrigues' formula
5

julia> x = Polynomial(:x)
Polynomial(1.0*x)

julia> derivative((x^2-1)^n, n) - 2^n *  factorial(n) * basis(Legendre, n)
LaurentPolynomial(0.0)

julia> p4, p5  =  basis.(Legendre, (4,5)) # verify  orthogonality  of  P₄,P₅
(Legendre(1.0⋅P₄(x)), Legendre(1.0⋅P₅(x)))

julia> SpecialPolynomials.innerproduct(Legendre, p4,  p5)
-1.111881270890998e-16
```
