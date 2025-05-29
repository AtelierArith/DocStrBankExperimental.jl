```
PieceType
```

チェスの駒のタイプを表す型です。

これは本質的に色のない駒です。可能な値は `PAWN`、`KNIGHT`、`BISHOP`、`ROOK`、`QUEEN`、`KING` および `PIECE_TYPE_NONE` です。`PIECE_TYPE_NONE` の存在理由は、チェスボードを駒の配列として表現し、ボード上の空のマスを示すために特別な `Piece` 値 `EMPTY` が必要だからです。`EMPTY` 駒のタイプは `PIECE_TYPE_NONE` です。
