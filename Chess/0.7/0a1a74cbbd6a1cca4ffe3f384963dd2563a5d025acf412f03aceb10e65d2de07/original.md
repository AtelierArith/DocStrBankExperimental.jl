```
PieceType
```

Type representing the type of a chess piece.

This is essentially a piece without color. The possible values are `PAWN`, `KNIGHT`, `BISHOP`, `ROOK`, `QUEEN`, `KING` and `PIECE_TYPE_NONE`. The reason for the existence of the value `PIECE_TYPE_NONE` is that we represent a chess board as an array of pieces, and we need a special `Piece` value `EMPTY` to indicate an empty square on the board. The type of the `EMPTY` piece is `PIECE_TYPE_NONE`
