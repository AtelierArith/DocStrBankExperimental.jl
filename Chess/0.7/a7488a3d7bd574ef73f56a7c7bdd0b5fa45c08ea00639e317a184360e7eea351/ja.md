```
to(m::Move)
```

移動の目的地のマス。

# 例

```julia-repl
julia> to(Move(SQ_G1, SQ_F3))
SQ_F3

julia> to(Move(SQ_C7, SQ_C8, QUEEN))
SQ_C8
true
```
