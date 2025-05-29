```
leading_term(p::AbstractPolynomialLike)
```

先頭項を返します。すなわち、`last(terms(p))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して `leading_term` を呼び出すと、$4x^2y$ が返されるべきです。
