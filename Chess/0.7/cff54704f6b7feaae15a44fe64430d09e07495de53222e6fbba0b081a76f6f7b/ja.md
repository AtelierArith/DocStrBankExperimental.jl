```
queens(b::Board, c::PieceColor)
```

指定された色のクイーンを含むマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> queens(b, WHITE) == SquareSet(SQ_D1)
true

julia> queens(b, BLACK) == SquareSet(SQ_D8)
true
```
