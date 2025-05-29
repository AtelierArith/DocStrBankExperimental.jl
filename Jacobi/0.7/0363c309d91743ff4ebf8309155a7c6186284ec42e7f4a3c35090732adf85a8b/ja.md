```
poly_jacobi(n, [::Type{T}=Int, [var=:x]])
```

次数 n のジャコビ多項式を `Polynomial` オブジェクトとして作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `a` ジャコビ多項式の重み α
  * `b` ジャコビ多項式の重み β
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_jacobi(4, 1, 1)
Polynomials.Polynomial(0.625 - 8.75*x^2 + 13.125*x^4)

julia> p2 = poly_jacobi(4, 1, 1, Rational{Int})
Polynomials.Polynomial(5//8 - 35//4*x^2 + 105//8*x^4)

julia> p3 = poly_jacobi(4, 1, 1, BigFloat, :y)
Polynomials.Polynomial(0.625 - 8.75*y^2 + 13.125*y^4)
```
