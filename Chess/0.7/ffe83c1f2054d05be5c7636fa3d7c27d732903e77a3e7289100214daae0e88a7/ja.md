```
bishoplike(b::Board, c::PieceColor)
```

与えられた色のビショップライクな駒を含むマスの集合。

ビショップライクな駒とは、ビショップのように動ける駒、すなわちビショップとクイーンです。

# 例

```julia-repl
julia> b = startboard();

julia> bishoplike(b, WHITE) == SquareSet(SQ_C1, SQ_D1, SQ_F1)
true

julia> bishoplike(b, BLACK) == SquareSet(SQ_C8, SQ_D8, SQ_F8)
true
```
