```
spolynomial(p::AbstractPolynomialLike, q::AbstractPolynomialLike)
```

`p` と `q` の S-多項式を計算します。定義は次の通りです。

$$
S(p, q) =  \frac{m}{\mathrm{\mathsc{LT}}(p)} \cdot p - \frac{m}{\mathrm{\mathsc{LT}}(q)} \cdot q
$$

ここで、$m = \mathrm{lcm}(\mathrm{\mathsc{LM}}(p), \mathrm{\mathsc{LM}}(q))$ です。
