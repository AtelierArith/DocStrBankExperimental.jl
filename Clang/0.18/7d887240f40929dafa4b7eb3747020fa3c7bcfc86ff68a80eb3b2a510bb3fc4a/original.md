```
search(cursors::Vector{CLCursor}, ismatch::Function) -> Vector{CLCursor}
```

Return vector of CLCursors that match predicate. `ismatch` is a function that accepts a CLCursor argument.
