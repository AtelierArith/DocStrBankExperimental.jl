```
to(m::Move)
```

The destination square of a move.

# Examples

```julia-repl
julia> to(Move(SQ_G1, SQ_F3))
SQ_F3

julia> to(Move(SQ_C7, SQ_C8, QUEEN))
SQ_C8
true
```
