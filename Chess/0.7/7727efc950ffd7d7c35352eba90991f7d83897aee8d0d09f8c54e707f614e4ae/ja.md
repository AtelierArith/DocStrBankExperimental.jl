```
ptype(p::Piece)
```

`Piece`の型を見つけます。

# 例

```julia-repl
julia> ptype(PIECE_BQ)
QUEEN

julia> ptype(EMPTY)
PIECE_TYPE_NONE
```
