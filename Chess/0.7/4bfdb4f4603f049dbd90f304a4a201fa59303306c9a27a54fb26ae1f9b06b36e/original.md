```
SquareDelta
```

A type representing the delta or vector between two squares.

A `SquareDelta` value is usually obtained either through one of the constants `DELTA_N`, `DELTA_S`, `DELTA_E`, `DELTA_W`, `DELTA_NW`, `DELTA_NE`, `DELTA_SW`, `DELTA_SE`, or by subtracting two square values.

It is possible to add or subtract two `SquareDelta`s, to multiply a `SquareDelta` by an integer scalar, or to add or subtract a `SquareDelta` to a `Square`.

# Examples

```julia-repl
julia> DELTA_N + DELTA_W == DELTA_NW
true

julia> SQ_D3 - SQ_C3 == DELTA_E
true

julia> SQ_G8 - 3 * DELTA_N
SQ_G5
```
