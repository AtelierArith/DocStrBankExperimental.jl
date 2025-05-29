```
coefficient(p::AbstractPolynomialLike, m::AbstractMonomialLike, vars)::AbstractPolynomialLike
```

多項式 `p` の単項式 `m` の係数を、変数 `vars` に関して多項式として考慮して返します。

### 例

`coefficient((a+b)x^2+2x+y*x^2, x^2, [x,y])` を呼び出すと `a+b` が返されるべきです。`coefficient((a+b)x^2+2x+y*x^2, x^2, [x])` を呼び出すと `a+b+y` が返されるべきです。
