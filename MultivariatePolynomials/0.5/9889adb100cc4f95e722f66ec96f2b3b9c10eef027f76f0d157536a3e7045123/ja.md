```
coefficient(t::AbstractTermLike)
```

項`t`の係数を返します。

```
coefficient(p::AbstractPolynomialLike, m::AbstractMonomialLike)
```

`p`の中の単項式`m`の係数を返します。

### 例

$$
4x^2y
$$

に対して`coefficient`を呼び出すと$4$が返されるべきです。`coefficient(2x + 4y^2 + 3, y^2)`を呼び出すと$4$が返されるべきです。`coefficient(2x + 4y^2 + 3, x^2)`を呼び出すと$0$が返されるべきです。
