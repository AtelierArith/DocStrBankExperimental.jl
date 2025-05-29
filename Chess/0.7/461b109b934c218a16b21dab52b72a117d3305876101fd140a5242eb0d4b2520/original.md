```
function movetosan(b::Board, m::Move)
```

Converts a move to a string in short algebraic notation.

# Examples

```julia-repl
julia> b = startboard();

julia> movetosan(b, Move(SQ_D2, SQ_D4))
"d4"
```
