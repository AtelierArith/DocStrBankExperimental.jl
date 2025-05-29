```
rooks(b::Board, c::PieceColor)
```

The set of squares containing rooks of the given color.

# Examples

```julia-repl
julia> b = startboard();

julia> rooks(b, WHITE) == SquareSet(SQ_A1, SQ_H1)
true

julia> rooks(b, BLACK) == SquareSet(SQ_A8, SQ_H8)
true
```
