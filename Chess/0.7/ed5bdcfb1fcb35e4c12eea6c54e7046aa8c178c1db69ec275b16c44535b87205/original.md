```
pieces(b::Board, c::PieceColor)
pieces(b::Board, t::PieceType)
pieces(b::Board, c::PieceColor, t::PieceType)
pieces(b::Board, p::Piece)
```

Obtain the set of squares containing various kinds of pieces.

# Examples

```julia-repl
julia> b = startboard();

julia> pieces(b, WHITE) == SS_RANK_1 ∪ SS_RANK_2
true

julia> pieces(b, ROOK) == SquareSet(SQ_A1, SQ_H1, SQ_A8, SQ_H8)
true

julia> pieces(b, BLACK, PAWN) == SS_RANK_7
true

julia> pieces(b, PIECE_WB)
SquareSet:
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  #  -  -  #  -  -
```
