```
pawns(b::Board, c::PieceColor)
```

指定された色のポーンが含まれるマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> pawns(b, WHITE) == SS_RANK_2
true

julia> pawns(b, BLACK) == SS_RANK_7
true
```
