```
rooklike(b::Board, c::PieceColor)
```

指定された色のルークライクな駒が含まれるマスの集合。

ルークライクな駒とは、ルークのように動ける駒、すなわちルークとクイーンです。

# 例

```julia-repl
julia> b = startboard();

julia> rooklike(b, WHITE) == SquareSet(SQ_A1, SQ_D1, SQ_H1)
true

julia> rooklike(b, BLACK) == SquareSet(SQ_A8, SQ_D8, SQ_H8)
true
```
