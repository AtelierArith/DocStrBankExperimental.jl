```
poly_djacobi(n, [::Type{T}=Int, [var=:x]])
```

次数 n のジャコビ多項式の導関数 `Polynomial` オブジェクトを作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `a` ジャコビ多項式の重み α
  * `b` ジャコビ多項式の重み β
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用される記号

# 例

```julia-repl
julia> p = poly_djacobi(4, 1, 1)
Polynomials.Polynomial(-17.5*x + 52.5*x^3)

julia> p2 = poly_djacobi(4, 1, 1, Rational{Int})
Polynomials.Polynomial(-35//2*x + 105//2*x^3)

julia> p3 = poly_djacobi(4, 1, 1, BigFloat, :y)
Polynomials.Polynomial(-17.5*y + 52.5*y^3)
```
