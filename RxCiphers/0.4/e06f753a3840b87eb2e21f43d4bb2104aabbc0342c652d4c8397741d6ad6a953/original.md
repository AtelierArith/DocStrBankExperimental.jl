```
untokenise(token::Int, W::AbstractCharSpace) -> String
```

Returns the substring that is assigned `token` in `W`

# Examples

```julia-repl
julia> untokenise(3, Alphabet)
"C"

julia> untokenise(15, Decimal^2)
"41"
```
