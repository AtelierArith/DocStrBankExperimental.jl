```
LorentzTransform(f::PiecewiseFunction, m::Integer [, ground::Real=1e-10])
```

Constructor of a `LorentzTransform` object for the piecewise function `f`. `m` is the order of the transform. The moment expansion is used if the result of the transform is smaller than `ground`.

## Fields

  * `f::PiecewiseFunction`
  * `m::Integer`
  * `ground::Real`
  * `moments::Vector{Real}`

## Example

$L^2$ transform of a box:

```julia-repl
julia> L = LorentzTransform(PiecewiseFunction(Piece((-1, 1), POLY, [1])), 2)
< L^2 transform of piecewise function with support [-1.0, 1.0] >

julia> L(0, -im)
0.13023806336711655
```
