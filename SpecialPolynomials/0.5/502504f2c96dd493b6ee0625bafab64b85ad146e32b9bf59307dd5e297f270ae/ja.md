```
エルミート
```

[エルミート](https://en.wikipedia.org/wiki/Hermite_polynomials)多項式には、物理学者向けのバージョン（`Hermite`または`H`）と確率論者向けのバージョン（`ChebyshevHermite`または`Hₑ`）の2つがあります。これらは、`Hᵢ(x) = 2^(i/2) Hₑᵢ(√2 x)`を通じて関連しています。

エルミート多項式の重み関数は`w(x)=exp(-x^2/2)`で、定義域は実数直線です。

## 例

```jldoctest
julia> using Polynomials,  SpecialPolynomials

julia> x = variable(Polynomial{Rational{Int}})
Polynomial(x)

julia> [basis(Hermite, i)(x) for i in 0:5]
6-element Vector{Polynomial{Float64, :x}}:
 Polynomial(1.0)
 Polynomial(2.0*x)
 Polynomial(-2.0 + 4.0*x^2)
 Polynomial(-12.0*x + 8.0*x^3)
 Polynomial(12.0 - 48.0*x^2 + 16.0*x^4)
 Polynomial(120.0*x - 160.0*x^3 + 32.0*x^5)

julia> [basis(ChebyshevHermite, i)(x) for i in 0:5]
6-element Vector{Polynomial{Float64, :x}}:
 Polynomial(1.0)
 Polynomial(1.0*x)
 Polynomial(-1.0 + 1.0*x^2)
 Polynomial(-3.0*x + 1.0*x^3)
 Polynomial(3.0 - 6.0*x^2 + 1.0*x^4)
 Polynomial(15.0*x - 10.0*x^3 + 1.0*x^5)
```

!!! note
    エルミートファミリーは助けが必要です。`Bn`と`Cn`の計算値は両方とも0です。

