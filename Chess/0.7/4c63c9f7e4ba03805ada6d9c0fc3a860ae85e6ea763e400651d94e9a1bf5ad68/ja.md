```
ispromotion(m::Move)
```

移動が昇格移動であるかどうかを判断します。

# 例

```julia-repl
julia> ispromotion(Move(SQ_G1, SQ_F3))
false

julia> ispromotion(Move(SQ_C7, SQ_C8, QUEEN))
true
```
