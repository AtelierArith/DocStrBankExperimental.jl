```
dateplayed(g::SimpleGame)::Union{Date, Nothing}
dateplayed(g::Game)::Union{Date, Nothing}
```

The date at which the game was played, or `nothing`.

This function makes use of the PGN date tag, trying to behave robustly with sensible defaults when the date is incomplete or incorrectly formatted. It handles both ISO format YYYY-MM-DD dates and PGN format YYYY.MM.DD dates. If either the month or the day is missing, they are replaced with 1. On failure, returns `nothing`.

# Examples

```julia-repl
julia> g = Game();

julia> setheadervalue!(g, "Date", "2019.09.20");

julia> dateplayed(g)
2019-09-20

julia> setheadervalue!(g, "Date", "2019.09.??");

julia> dateplayed(g)
2019-09-01

julia> setheadervalue!(g, "Date", "2019.??.??");

julia> dateplayed(g)
2019-01-01

julia> setheadervalue!(g, "Date", "*");

julia> dateplayed(g) == nothing
true
```
