```
pawns(b::Board, c::PieceColor)
```

The set of squares containing pawns of the given color.

# Examples

```julia-repl
julia> b = startboard();

julia> pawns(b, WHITE) == SS_RANK_2
true

julia> pawns(b, BLACK) == SS_RANK_7
true
```
