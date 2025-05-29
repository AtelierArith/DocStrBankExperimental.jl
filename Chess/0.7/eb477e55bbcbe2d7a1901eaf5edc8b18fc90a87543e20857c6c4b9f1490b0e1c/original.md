```
knights(b::Board, c::PieceColor)
```

The set of squares containing knights of the given color.

# Examples

```julia-repl
julia> b = startboard();

julia> knights(b, WHITE) == SquareSet(SQ_B1, SQ_G1)
true

julia> knights(b, BLACK) == SquareSet(SQ_B8, SQ_G8)
true
```
