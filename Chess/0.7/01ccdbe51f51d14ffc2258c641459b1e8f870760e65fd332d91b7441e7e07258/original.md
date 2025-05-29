```
PieceColor
```

Type representing the color of a chess piece.

The possible values are `WHITE`, `BLACK` and `COLOR_NONE`. The reason for the existence of the value `COLOR_NONE` is that we represent a chess board as an array of pieces, and we need a special `Piece` value `EMPTY` to indicate an empty square on the board. The color of the `EMPTY` piece is `COLOR_NONE`.
