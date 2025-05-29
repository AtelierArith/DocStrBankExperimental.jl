```
setdateplayed!(g::SimpleGame, date::Date)
setdateplayed!(g::Game, date::Date)
```

Set the "Date" header to the given date, using the standard PGN date format.

# Examples

```julia-repl
julia> using Dates

julia> g = Game();

julia> setdateplayed!(g, Date(2020, 10, 08));

julia> headervalue(g, "Date")
"2020.10.08"

julia> dateplayed(g)
2020-10-08
```
