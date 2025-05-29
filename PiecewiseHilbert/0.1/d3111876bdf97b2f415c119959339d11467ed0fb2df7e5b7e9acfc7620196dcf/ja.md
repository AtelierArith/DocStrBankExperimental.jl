```
hilbert_transform(f::PiecewiseFunction, z::Complex)
```

区分的関数 `f` のヒルベルト変換を複素数 `z` で計算します：

$$
(H\circ f)(z) = \int_{-\infty}^{\infty}dx\,\frac{f(x)}{z-x}
$$

## 例

```julia-repl
julia> hilbert_transform(PiecewiseFunction([Piece((-1, 1), POLY, [1])]), im)
0.0 - 1.5707963267948966im
```
