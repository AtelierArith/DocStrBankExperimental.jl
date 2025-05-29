```
tokenise(s::String, W::AbstractCharSpace) -> Int, Nothing
```

Returns the token assigned to `s`

Returns `nothing` if `s` is not in `W`

# Examples

```julia-repl
julia> tokenise("C", Alphabet)
3

julia> tokenise("1", Alphabet)

julia> tokenise("01", Decimal^2)
11

```
