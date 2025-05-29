```
coloropp(c::PieceColor)
```

色の反対を返します。

# 例

```julia-repl
julia> coloropp(WHITE) == BLACK
true

julia> coloropp(BLACK) == WHITE
true
```
