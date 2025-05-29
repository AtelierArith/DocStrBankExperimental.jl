```
nterms(p::AbstractPolynomialLike)
```

`p`の非ゼロ項の数を返します。すなわち、`length(terms(p))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`nterms`を呼び出すと、3が返されるべきです。
