```
coefficients(p::AbstractPolynomialLike)
```

`p`の非ゼロ項の係数に対するイテレータを返します。多項式は降順の単項式順にソートされています。

```
coefficients(p::AbstractPolynomialLike, X::AbstractVector)
```

`X`が必ずしもソートされていないが重複エントリのない単項式ベクトルであるとき、`p`の中の`X`の単項式の係数に対するイテレータを返します。

### 例

$$
4x^2y + xy + 2x
$$

に対して`coefficients`を呼び出すと、$[4, 1, 2]$のイテレータが返されるべきです。`coefficients(4x^2*y + x*y + 2x + 3, [x, 1, x*y, y])`を呼び出すと、$[2, 3, 1, 0]$のイテレータが返されるべきです。
