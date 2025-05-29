```
shift_e(ss::SquareSet)
```

Shift the square set one step in the 'east' direction.

Squares that are shifted off the edge of the board disappear.

# Examples

```julia-repl
julia> shift_e(SS_FILE_F) == SS_FILE_G
true

julia> shift_e(SquareSet(SQ_F5, SQ_G6, SQ_H7)) == SquareSet(SQ_G5, SQ_H6)
true
```
