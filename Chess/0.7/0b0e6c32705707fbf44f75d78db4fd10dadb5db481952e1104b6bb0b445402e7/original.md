```
kings(b::Board, c::PieceColor)
```

The set of squares containing kings of the given color.

Unless something is very wrong, this set should always contain exactly one square.

# Examples

```julia-repl
julia> b = startboard();

julia> kings(b, WHITE) == SquareSet(SQ_E1)
true

julia> kings(b, BLACK) == SquareSet(SQ_E8)
true
```
