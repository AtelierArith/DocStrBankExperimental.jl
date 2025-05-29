```
PiecewiseFunction([parity::Symbol,] pieces::Vector{Piece})
```

Constructor of a `PiecewiseFunction`. The optional argument `parity` is `:none` (default), `:even`, or `:odd`. The argument `pieces` contains the various pieces (see [`Piece`](@ref)).

## Fields

  * `parity::Symbol`
  * `pieces::Vector{Piece}`

## Example

This represents the Cauchy principal value of $1/x$:

```julia-repl
julia> f = PiecewiseFunction(:odd, Piece((0, Inf), (false, true), x -> 1 / x))
< Piecewise odd function with 1 piece and support [-Inf, Inf] >

julia> f.([-1, 0, 1])
3-element Vector{Real}:
 -1.0
  0
  1.0

```
