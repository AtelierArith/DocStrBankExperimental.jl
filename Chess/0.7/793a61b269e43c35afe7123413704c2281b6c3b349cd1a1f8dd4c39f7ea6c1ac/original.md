```
shift_n(ss::SquareSet)
```

Shift the square set one step in the 'north' direction.

Squares that are shifted off the edge of the board disappear.

```julia-repl
julia> shift_n(SS_RANK_2) == SS_RANK_3
true

julia> shift_n(SquareSet(SQ_D3, SQ_E4, SQ_F8)) == SquareSet(SQ_D4, SQ_E5)
true
```
