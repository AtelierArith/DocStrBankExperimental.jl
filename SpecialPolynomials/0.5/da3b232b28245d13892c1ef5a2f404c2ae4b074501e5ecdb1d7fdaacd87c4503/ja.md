Laguerre{α, T <: Number}

ラゲール多項式は、ドメイン `[0, oo)` 上で重み関数 `x^α * exp(-x)` を持ちます。パラメータ `α` はコンストラクタを通じて指定されます。

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = Laguerre{1/2}([1,2,3])
Laguerre{0.5}(1⋅Lᵅ₀(x) + 2⋅Lᵅ₁(x) + 3⋅Lᵅ₂(x))

julia> convert(Polynomial, p)
Polynomial(9.625 - 9.5*x + 1.5*x^2)
```

ラゲール多項式は `α=0` の場合です。

```jldoctest
julia> using Polynomials, SpecialPolynomials

julia> p = Laguerre{0}([1,2,3])
Laguerre{0}(1⋅L₀(x) + 2⋅L₁(x) + 3⋅L₂(x))

julia> convert(Polynomial, p)
Polynomial(6.0 - 8.0*x + 1.5*x^2)

julia> phi(u, i) = derivative(u) -  u # 小さい n のためのロドリゲスの公式を検証; n! L_n = (d/dx-1)^n x^n
phi (generic function with 1 method)

julia> x = Polynomial(:x)
Polynomial(1.0*x)

julia> n = 7
7

julia> factorial(n) * basis(Laguerre{0}, n) - foldl(phi, 1:n, init=x^n)
LaurentPolynomial(-5.4569682106375694e-12 + 1.4551915228366852e-11*x - 7.275957614183426e-12*x²)
```
