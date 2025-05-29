```
nflverse_game_id(season::Number,week::Number,away::AbstractString,home::AbstractString)
```

Check and calculate an nflverse game ID.

# Examples

```julia-repl
julia> nflverse_game_id(2022, 2, "LAC", "KC")
"2022_02_LAC_KC"
```
