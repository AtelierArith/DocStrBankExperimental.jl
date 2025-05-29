```
rooklike(b::Board, c::PieceColor)
```

The set of squares containing rooklike pieces of the given color.

The rooklike pieces are the pieces that can move like a rook, i.e. rooks and queens.

# Examples

```julia-repl
julia> b = startboard();

julia> rooklike(b, WHITE) == SquareSet(SQ_A1, SQ_D1, SQ_H1)
true

julia> rooklike(b, BLACK) == SquareSet(SQ_A8, SQ_D8, SQ_H8)
true
```
