```
isok(s::Square)
```

Tests whether a `Square` has a valid value.

# Examples

```julia-repl
julia> isok(SQ_G7)
true

julia> isok(Square(42))
true

julia> isok(Square(100))
false

julia> isok(Square(0))
false
```
