```
ispromotion(m::Move)
```

Determine whether a move is a promotion move.

# Examples

```julia-repl
julia> ispromotion(Move(SQ_G1, SQ_F3))
false

julia> ispromotion(Move(SQ_C7, SQ_C8, QUEEN))
true
```
