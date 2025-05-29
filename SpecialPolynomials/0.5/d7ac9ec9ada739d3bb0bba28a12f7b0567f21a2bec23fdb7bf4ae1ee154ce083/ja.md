```
ChebyshevU{T}
```

第二種の[チェビシェフ](https://en.wikipedia.org/wiki/Chebyshev_polynomials)多項式を実装します。これらは、定義域`[-1,1]`において重み関数`w(x) = sqrt(1-x^2)`を持ちます。

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = ChebyshevU([1,2,3])
ChebyshevU(1⋅U₀(x) + 2⋅U₁(x) + 3⋅U₂(x))

julia> convert(Polynomial, p)
Polynomial(-2.0 + 4.0*x + 12.0*x^2)

julia> derivative(p)
ChebyshevU(4.0⋅U₀(x) + 12.0⋅U₁(x))

julia> roots(p)
2-element Vector{ComplexF64}:
 -0.6076252185107651 + 0.0im
 0.27429188517743175 + 0.0im
```
