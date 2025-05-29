```
movefromstring(s::String)
```

Convert a UCI move string to a move.

Returns `nothing` if the input string is not a valid UCI move.

# Examples

```julia-repl
julia> movefromstring("d2d4") == Move(SQ_D2, SQ_D4)
true

julia> movefromstring("h7h8q") == Move(SQ_H7, SQ_H8, QUEEN)
true

julia> movefromstring("f7f9") == nothing
true

julia> movefromstring("") == nothing
true
```
