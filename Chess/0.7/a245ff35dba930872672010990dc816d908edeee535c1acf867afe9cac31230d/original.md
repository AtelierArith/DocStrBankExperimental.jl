```
sidetomove(b::Board)
```

The current side to move, `WHITE` or `BLACK`.

# Examples

```julia-repl
julia> b = startboard();

julia> b2 = domove(b, "e4");

julia> sidetomove(b)
WHITE

julia> sidetomove(b2)
BLACK
```
