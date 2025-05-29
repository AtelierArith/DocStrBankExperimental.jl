```
poly_dlegendre(n, [::Type{T}=Int, [var=:x]])
```

次数 n のレジェンドル多項式の導関数 `Polynomial` オブジェクトを作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_dlegendre(4)
Polynomials.Polynomial(-7.5*x + 17.5*x^3)

julia> p2 = poly_dlegendre(4, Rational{Int})
Polynomials.Polynomial(-15//2*x + 35//2*x^3)

julia> p3 = poly_dlegendre(4, BigFloat, :y)
Polynomials.Polynomial(-7.5*y + 17.5*y^3)
```
