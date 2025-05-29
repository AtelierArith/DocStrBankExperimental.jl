```
PieceColor
```

チェスの駒の色を表す型です。

可能な値は `WHITE`、`BLACK`、および `COLOR_NONE` です。`COLOR_NONE` の存在理由は、チェスボードを駒の配列として表現し、ボード上の空のマスを示すために特別な `Piece` 値 `EMPTY` が必要だからです。`EMPTY` 駒の色は `COLOR_NONE` です。
