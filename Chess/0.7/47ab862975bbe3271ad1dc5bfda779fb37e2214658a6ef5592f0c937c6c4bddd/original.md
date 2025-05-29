```
tostring(m::Move)
```

Convert a move to a string in UCI notation.

# Examples

```julia-repl
julia> tostring(Move(SQ_G1, SQ_F3))
"g1f3"

julia> tostring(Move(SQ_E2, SQ_E1, KNIGHT))
"e2e1n"
```
