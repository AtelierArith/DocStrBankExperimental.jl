```
shift_s(ss::SquareSet)
```

Shift the square set one step in the 'south' direction.

Squares that are shifted off the edge of the board disappear.

# Examples

```julia-repl
julia> shift_s(SS_RANK_3) == SS_RANK_2
true

julia> shift_s(SquareSet(SQ_C3, SQ_D2, SQ_E1)) == SquareSet(SQ_C2, SQ_D1)
true
```
