```
promotion(m::Move)
```

Find the promotion piece type of a move.

Use this function only after first using `ispromotion` to determine whether the move is a promotion move at all.

# Examples

```julia-repl
julia> promotion(Move(SQ_C7, SQ_C8, QUEEN))
QUEEN

julia> promotion(Move(SQ_B2, SQ_B1, KNIGHT))
KNIGHT
```
