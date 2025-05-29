```
clean_team_abbrs(team::AbstractString; current_location::Bool = true, keep_non_matches::Bool = true)
```

Clean abbreviations of teams to NFLverse friendly abbreviations.

# Examples

```julia-repl
julia> clean_team_abbrs("SD")
"LAC"
```
