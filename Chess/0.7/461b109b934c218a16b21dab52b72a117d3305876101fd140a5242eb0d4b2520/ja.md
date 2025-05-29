```
function movetosan(b::Board, m::Move)
```

移動を短い代数表記の文字列に変換します。

# 例

```julia-repl
julia> b = startboard();

julia> movetosan(b, Move(SQ_D2, SQ_D4))
"d4"
```
