```
kings(b::Board, c::PieceColor)
```

指定された色の王が含まれているマスの集合。

何か非常に間違っていない限り、この集合には常に正確に1つのマスが含まれているはずです。

# 例

```julia-repl
julia> b = startboard();

julia> kings(b, WHITE) == SquareSet(SQ_E1)
true

julia> kings(b, BLACK) == SquareSet(SQ_E8)
true
```
