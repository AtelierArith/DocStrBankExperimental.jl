```
Jacobi{α,  β, T}
```

[Jacobi](https://en.wikipedia.org/wiki/Jacobi_polynomials) 多項式を実装します。これらは、定義域 `[-1,1]` において重み関数 `w(x) = (1-x)^α ⋅ (1+x)^β` を持ちます。多くの直交多項式のタイプは特別なケースです。パラメータはコンストラクタに指定されます：

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

特別なケースには `Jacobi{α-1/2,α-1/2} = Gegenbauer{α}`、`Jacobi{-1/2,-1/2} = Chebyshev`、`Jacobi{1/2,1/2} = ChebyshevU`、および `Jacobi{0,0} = Legendre` が含まれます。
