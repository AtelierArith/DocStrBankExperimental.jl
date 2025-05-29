```
lorentz_transform(f::PiecewiseFunction, m::Integer, y::Real, z::Complex)
```

``Lorentz transform of the piecewise function`f`:

$$
(L^m\circ f)(y, z) = \int_{-\infty}^{\infty}dx\,f(x)\left[\frac{\mathrm{Im}
\,z/\pi}{(y-\mathrm{Re}\,z-x)^2+(\mathrm{Im}\,z)^2}\right]^m
$$

## Example

```julia-repl
julia> lorentz_transform(PiecewiseFunction([Piece((-1, 1), POLY, [1])]), 2, 0, -im)
0.13023806336711655
```
