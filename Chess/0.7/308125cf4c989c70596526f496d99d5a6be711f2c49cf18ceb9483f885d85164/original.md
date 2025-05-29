```
pawns(b::Board)
```

The set of squares containing pawns of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> pawns(b) == SS_RANK_2 ∪ SS_RANK_7
true
```
