```
isempty(ss::SquareSet)
```

Determine whether a square set is the empty set.

# Examples

```julia-repl
julia> isempty(SS_RANK_1)
false

julia> isempty(SS_EMPTY)
true

julia> isempty(SS_RANK_1 ∩ SS_RANK_2)
true
```
