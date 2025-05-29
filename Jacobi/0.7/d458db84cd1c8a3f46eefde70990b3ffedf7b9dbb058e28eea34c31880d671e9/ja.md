```
poly_legendre(n, [::Type{T}=Int, [var=:x]])
```

次数 n のレジェンドル多項式 `Polynomial` オブジェクトを作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_legendre(4)
Polynomials.Polynomial(0.375 - 3.75*x^2 + 4.375*x^4)

julia> p2 = poly_legendre(4, Rational{Int})
Polynomials.Polynomial(3//8 - 15//4*x^2 + 35//8*x^4)

julia> p3 = poly_legendre(4, BigFloat, :y)
Polynomials.Polynomial(0.375 - 3.75*y^2 + 4.375*y^4)
```
