```
occupiedsquares(b::Board)
```

The set of all occupied squares on the board.

# Examples

```julia-repl
julia> b = startboard();

julia> occupiedsquares(b) == pieces(b, WHITE) ∪ pieces(b, BLACK)
true

julia> isempty(emptysquares(b) ∩ occupiedsquares(b))
true
```
