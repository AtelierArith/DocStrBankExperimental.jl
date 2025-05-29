```
bishops(b::Board, c::PieceColor)
```

指定された色のビショップが含まれるマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> bishops(b, WHITE) == SquareSet(SQ_C1, SQ_F1)
true

julia> bishops(b, BLACK) == SquareSet(SQ_C8, SQ_F8)
true
```
