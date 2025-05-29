```
integraltransform(f::PiecewiseFunction, X::Any)
```

Integral transform of the piecewise function `f`, defined as

$$
(K\circ f)(\mathbf{X}) = \int_{-\infty}^{\infty}dx\,f(x)K(x,\mathbf{X}).
$$

This method assumes that each function `F(::Real, ::Vector{Any})` used in the piecewise function `f` has a method `F(::Real, ::Vector{Any}, ::Any)` that returns the primitive of $F(x, \mathbf{a})$ over the kernel $K(x, \mathbf{X})$, i.e., `d/dx F(x, a, X) = F(x, a) * K(x, X)`. If `f.parity` is `:even` or `:odd`, `integraltransform` requires a method `F(::Integer, ::Real, ::Vector{Any}, ::Any)` such that `d/dx F(1, x, a, X) = F(x, a) * (K(x, X) +  K(-x, X))` and `d/dx F(-1, x, a, X) = F(x, a) * (K(x, X) - K(-x, X))`.

## Example

This define a `Formula` object `LIN` that can be used to represent any piecewise linear function, and such that `integraltransform` provides its Fourier transform:

```julia-repl
julia> F(x, a) = a[1] + a[2] * x;
       LIN = Formula("LIN", 2, F, (a, s) -> a * s, a -> [a[1], -a[2]]);
       F(x, a, k) = (a[1] * k + a[2] * (k * x + im)) * exp(im * k * x)/(im * k^2);
       F(s, x, a, k) = 2 * (s == 1 ? real(F(x, a, k)) : im * imag(F(x, a, k)));
       f = PiecewiseFunction(:even, [Piece((0, π), LIN, [π, -1])])
< Piecewise even function with 1 piece and support [-3.1416, 3.1416] >

julia> integraltransform(f, 1)
4.0
```
