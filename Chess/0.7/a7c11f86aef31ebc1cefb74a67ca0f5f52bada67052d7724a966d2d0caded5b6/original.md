```
isok(f::SquareFile)
```

Tests whether a `SquareFile` contains a valid value.

# Examples

```julia-repl
julia> isok(FILE_A)
true

julia> isok(SquareFile(0))
false
```
