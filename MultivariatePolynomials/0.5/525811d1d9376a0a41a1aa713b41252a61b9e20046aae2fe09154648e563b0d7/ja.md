```
terms(p::AbstractPolynomialLike)
```

多項式 `p` の非ゼロ項に対するイテレータを、降順の単項式順序で返します。

### 例

$$
4x^2y + xy + 2x
$$

に対して `terms` を呼び出すと、$[4x^2y, xy, 2x]$ のイテレータが返されるべきです。
