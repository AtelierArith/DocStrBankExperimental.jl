```
LaurentPolynomial{T,X}(coeffs::AbstractVector, [m::Integer = 0], [var = :x])
```

[ローレンツ](https://en.wikipedia.org/wiki/Laurent_polynomial)多項式は、`a_{m}x^m + ... + a_{n}x^n`の形をしており、ここで`m,n`は整数（必ずしも正である必要はない）で、`m <= n`です。

`coeffs`は`a_{m}, a_{m-1}, ..., a_{n}`を指定します。引数`m`は、系列における変数の最小指数を表し、デフォルトではゼロと見なされます。

ローレンツ多項式と標準基底多項式は、ローレンツ多項式に昇格します。ローレンツ多項式は、`m >= 0`のときに標準基底多項式に変換できます。

多項式に`x⁻¹`項がある場合、積分は失敗します。

!!! note
    `LaurentPolynomial`は、このパッケージの他の多項式タイプとは異なり、軸を意識しています。


# 例:

```jldoctest
julia> using Polynomials

julia> P = LaurentPolynomial;

julia> p = P([1,1,1],  -1)
LaurentPolynomial(x⁻¹ + 1 + x)

julia> q = P([1,1,1])
LaurentPolynomial(1 + x + x²)

julia> pp = Polynomial([1,1,1])
Polynomial(1 + x + x^2)

julia> p + q
LaurentPolynomial(x⁻¹ + 2 + 2*x + x²)

julia> p * q
LaurentPolynomial(x⁻¹ + 2 + 3*x + 2*x² + x³)

julia> p * pp
LaurentPolynomial(x⁻¹ + 2 + 3*x + 2*x² + x³)

julia> pp - q
LaurentPolynomial(0)

julia> derivative(p)
LaurentPolynomial(-x⁻² + 1)

julia> integrate(q)
LaurentPolynomial(1.0*x + 0.5*x² + 0.3333333333333333*x³)

julia> integrate(p)  # x⁻¹  項は問題です
ERROR: ArgumentError: Can't integrate Laurent polynomial with  `x⁻¹` term
[...]

julia> integrate(P([1,1,1], -5))
LaurentPolynomial(-0.25*x⁻⁴ - 0.3333333333333333*x⁻³ - 0.5*x⁻²)

julia> x⁻¹ = inv(variable(LaurentPolynomial)) # `inv`は単項式に対して定義されています
LaurentPolynomial(1.0*x⁻¹)

julia> p = Polynomial([1,2,3])
Polynomial(1 + 2*x + 3*x^2)

julia> x = variable()
Polynomial(x)

julia> x^degree(p) * p(x⁻¹) # 係数を逆転させます
LaurentPolynomial(3.0 + 2.0*x + 1.0*x²)
```
