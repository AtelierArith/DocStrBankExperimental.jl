```
poly_dchebyshev(n, [::Type{T}=Int, [var=:x]])
```

次数 n のチェビシェフ多項式の導関数を `Polynomial` オブジェクトとして作成します。

特定の点で多項式を計算する代わりに、`Polynomials` パッケージを使用して実際の多項式を計算します。

パラメータ:

  * `n` 多項式の次数
  * `T` 多項式係数の型
  * `var` 多項式で変数として使用されるシンボル

# 例

```julia-repl
julia> p = poly_dchebyshev(4)
Polynomials.Polynomial(-16*x + 32*x^3)

julia> p2 = poly_dchebyshev(4, BigInt)
Polynomials.Polynomial(-16*x + 32*x^3)

julia> p3 = poly_dchebyshev(4, Float64, :y)
Polynomials.Polynomial(-16.0*y + 32.0*y^3)
```
