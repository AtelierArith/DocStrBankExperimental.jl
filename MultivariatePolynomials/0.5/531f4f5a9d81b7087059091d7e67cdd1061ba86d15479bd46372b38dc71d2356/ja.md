```
remove_leading_term(p::AbstractPolynomialLike)
```

多項式 `p` の先頭項を削除した多項式を返します。

### 例

$$
4x^2y + xy + 2x
$$

に対して `remove_leading_term` を呼び出すと、$xy + 2x$ が返されるべきです。
