```
bishops(b::Board)
```

The set of squares containing bishops of either color.

# Examples

```julia-repl
julia> b = startboard();

julia> bishops(b) == SquareSet(SQ_C1, SQ_F1, SQ_C8, SQ_F8)
true
```
