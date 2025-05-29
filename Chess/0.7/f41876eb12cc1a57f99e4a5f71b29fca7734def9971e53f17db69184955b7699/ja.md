```
rooks(b::Board, c::PieceColor)
```

指定された色のルークが含まれるマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> rooks(b, WHITE) == SquareSet(SQ_A1, SQ_H1)
true

julia> rooks(b, BLACK) == SquareSet(SQ_A8, SQ_H8)
true
```
