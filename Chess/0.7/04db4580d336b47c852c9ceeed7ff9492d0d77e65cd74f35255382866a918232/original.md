```
rankfromchar(c::Char)
```

Tries to convert a character to a rank.

The return value is a `Union{SquareRank, Nothing}`. The `nothing` is returned in case the character does not represent a valid rank.

# Examples

```julia-repl
julia> rankfromchar('2')
RANK_2

julia> rankfromchar('x') == nothing
true
```
