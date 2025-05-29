```
filesquares(f::SquareFile)
filesquares(s::Square)
```

The set of all squares on the provided file.

# Examples

```julia-repl
julia> filesquares(FILE_G) == SS_FILE_G
true

julia> filesquares(SQ_C5) == SS_FILE_C
true
```
