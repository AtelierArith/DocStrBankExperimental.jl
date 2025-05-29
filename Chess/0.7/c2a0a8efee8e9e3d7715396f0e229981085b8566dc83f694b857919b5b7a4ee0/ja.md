```
kingsquare(b::Board, c::PieceColor)
```

与えられた側の王の位置。

# 例

```julia-repl
julia> b = startboard();

julia> kingsquare(b, WHITE)
SQ_E1

julia> kingsquare(b, BLACK)
SQ_E8
```
