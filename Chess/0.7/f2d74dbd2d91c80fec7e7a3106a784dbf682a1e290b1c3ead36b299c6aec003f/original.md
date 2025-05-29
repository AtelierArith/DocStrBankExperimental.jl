```
ranksquares(r::SquareRank)
ranksquares(s::Square)
```

The set of all squares on the provided rank.

# Examples

```julia-repl
julia> ranksquares(RANK_2) == SS_RANK_2
true

julia> ranksquares(SQ_C5) == SS_RANK_5
true
```
