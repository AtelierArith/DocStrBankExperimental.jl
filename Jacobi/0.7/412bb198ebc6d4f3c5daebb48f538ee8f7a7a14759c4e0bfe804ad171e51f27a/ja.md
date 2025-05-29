```
poly_chebyshev2(n, [::Type{T}=Int, [var=:x]])
```

次数 n のチェビシェフ多項式（第二種）の `Polynomial` オブジェクトを作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_chebyshev2(4)
Polynomials.Polynomial(1 - 12*x^2 + 16*x^4)

julia> p2 = poly_chebyshev2(4, BigInt)
Polynomials.Polynomial(1 - 12*x^2 + 16*x^4)

julia> p3 = poly_chebyshev2(4, Float64, :y)
Polynomials.Polynomial(1.0 - 12.0*y^2 + 16.0*y^4)
```
