```
leading_coefficient(p::AbstractPolynomialLike)
```

`p`の先頭項の係数を返します。すなわち、`coefficient(leading_term(p))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`leading_coefficient`を呼び出すと$4$が返され、$0$に対して呼び出すと$0$が返されるべきです。
