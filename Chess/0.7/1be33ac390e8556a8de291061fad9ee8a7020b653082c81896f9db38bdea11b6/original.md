```
movefromsan(b::Board, san::String, movelist::MoveList)::Union{Move,Nothing}
movefromsan(b::Board, san::String)::Union{Move,Nothing}
```

Tries to read a move in Short Algebraic Notation.

Returns `nothing` if the provided string is an impossible or ambiguous move.

This internally calls `moves`, which can be supplied a pre-allocated `MoveList` in order to save time/space due to unnecessary allocations. If provided, the `movelist` parameter will be passed to `moves`. It is up to the caller to ensure that `movelist` has sufficient capacity.

# Examples

```julia-repl
julia> movefromsan(b, "Nf3")
Move(g1f3)

julia> movelist = MoveList(200)
0-element MoveList

julia> movefromsan(b, "Nf3", movelist)
Move(g1f3)

julia> movefromsan(b, "???") == nothing
true
```
