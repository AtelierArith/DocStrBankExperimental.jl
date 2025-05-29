```
poly_chebyshev(n, [::Type{T}=Int, [var=:x]])
```

次数 n のチェビシェフ多項式 `Polynomial` オブジェクトを作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ：

  * `n` 多項式の次数
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_chebyshev(4)
Polynomials.Polynomial(1 - 8*x^2 + 8*x^4)

julia> p2 = poly_chebyshev(4, BigInt)
Polynomials.Polynomial(1 - 8*x^2 + 8*x^4)

julia> p3 = poly_chebyshev(4, Float64, :y)
Polynomials.Polynomial(1.0 - 8.0*y^2 + 8.0*y^4)

```
