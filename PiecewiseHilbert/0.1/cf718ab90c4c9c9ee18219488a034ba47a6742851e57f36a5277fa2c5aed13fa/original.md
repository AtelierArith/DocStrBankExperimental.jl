```
HilbertTransform(f::PiecewiseFunction [, radius::Real])
```

Constructor of a `HilbertTransform` object for the piecewise function `f`. The moment expansion is used beyond |z| = radius in the complex plane. If not specified, the radius is set automatically. The field `error` gives an estimate of the absolute error at |z| = radius.

## Fields

  * `f::PiecewiseFunction`
  * `radius::Real`
  * `moments::Vector{Real}`
  * `error::Real`

## Example

Hilbert transform of a box:

```julia-repl
julia> H = HilbertTransform(PiecewiseFunction(Piece((-1, 1), POLY, [1])))
< Hilbert transform of piecewise function with support [-1.0, 1.0] >

julia> H.([1im, 10im, 100im])
3-element Vector{ComplexF64}:
 0.0 - 1.5707963267948966im
 0.0 - 0.19933730476190478im
 0.0 - 0.019999333333333334im
```
