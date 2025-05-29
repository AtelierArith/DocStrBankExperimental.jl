```
leading_monomial(p::AbstractPolynomialLike)
```

`p`の先頭項の単項式を返します。すなわち、`monomial(leading_term(p))`または`last(monomials(p))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`leading_monomial`を呼び出すと、$x^2y$が返されるべきです。
