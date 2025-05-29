```
Polynomial(p::MultivariatePolynomials.AbstractPolynomial [, variables [, homogenized=false]])
```

多変数多項式の高速評価のための構造体です。項はまず総次数で、次に辞書式順序でソートされます。`Polynomial`は[同次多項式](https://en.wikipedia.org/wiki/Homogeneous_polynomial)に対して第一級のサポートを持っています。このフィールドは、最初の変数を同次化変数として考慮するべきかどうかを示します。

```
Polynomial{T}(p::MultivariatePolynomials.AbstractPolynomial [, variables [, homogenized=false]])
```

係数の型`T`を強制することができます。最適なパフォーマンスのために、`T`は評価に使用される入力と同じ型であるべきです。

```
Polynomial(exponents::Matrix{Int}, coefficients::Vector{T}, variables, [, homogenized=false])
```

多項式を直接作成することもできます。指数の各列は項の指数を表すことに注意してください。

### 例

```
Poly([3 1; 1 1; 0 2 ], [-2.0, 3.0], [:x, :y, :z]) == 3.0x^2yz^2 - 2x^3y
```
