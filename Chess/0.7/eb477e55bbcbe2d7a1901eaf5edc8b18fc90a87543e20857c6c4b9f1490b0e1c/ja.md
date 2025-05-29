```
knights(b::Board, c::PieceColor)
```

指定された色のナイトが含まれるマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> knights(b, WHITE) == SquareSet(SQ_B1, SQ_G1)
true

julia> knights(b, BLACK) == SquareSet(SQ_B8, SQ_G8)
true
```
