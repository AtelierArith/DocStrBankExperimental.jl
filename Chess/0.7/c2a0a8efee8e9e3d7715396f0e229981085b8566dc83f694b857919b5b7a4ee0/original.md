```
kingsquare(b::Board, c::PieceColor)
```

The square of the king for the given side.

# Examples

```julia-repl
julia> b = startboard();

julia> kingsquare(b, WHITE)
SQ_E1

julia> kingsquare(b, BLACK)
SQ_E8
```
