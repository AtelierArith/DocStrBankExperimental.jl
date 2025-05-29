```
hilbert_transform(f::PiecewiseFunction, z::Complex)
```

Hilbert transform of the piecewise function `f` at the complex number `z`:

$$
(H\circ f)(z) = \int_{-\infty}^{\infty}dx\,\frac{f(x)}{z-x}
$$

## Example

```julia-repl
julia> hilbert_transform(PiecewiseFunction([Piece((-1, 1), POLY, [1])]), im)
0.0 - 1.5707963267948966im
```
