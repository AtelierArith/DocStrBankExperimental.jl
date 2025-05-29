```
tostring(m::Move)
```

移動をUCI表記の文字列に変換します。

# 例

```julia-repl
julia> tostring(Move(SQ_G1, SQ_F3))
"g1f3"

julia> tostring(Move(SQ_E2, SQ_E1, KNIGHT))
"e2e1n"
```
