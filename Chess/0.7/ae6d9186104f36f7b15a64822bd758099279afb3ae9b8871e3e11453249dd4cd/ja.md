```
isok(t::PieceType)
```

`PieceType` 値が有効かどうかをテストします。

`PAWN`、`KNIGHT`、`BISHOP`、`ROOK`、`QUEEN`、および `KING` のすべてに対して `true` を返し、その他の入力に対しては `false` を返します。

# 例

```julia-repl
julia> isok(QUEEN)
true

julia> isok(KNIGHT)
true

julia> isok(PIECE_TYPE_NONE)
false

julia> isok(PieceType(-1))
false
```
