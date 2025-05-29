```
queens(b::Board, c::PieceColor)
```

The set of squares containing queens of the given color.

# Examples

```julia-repl
julia> b = startboard();

julia> queens(b, WHITE) == SquareSet(SQ_D1)
true

julia> queens(b, BLACK) == SquareSet(SQ_D8)
true
```
