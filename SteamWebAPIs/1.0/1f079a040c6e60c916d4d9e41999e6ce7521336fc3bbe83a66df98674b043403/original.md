```
get_global_achievement_percentages_for_app(gameid::Int)::Dict{String,Float16}
```

**Summary**: `get_global_achievement_percentages_for_app` returns on global achievements overview of a specific game in percentages.

# Arguments

  * `gameid`: GameID to retrieve the achievement percentages for.

# Example

```julia-repl
julia> get_global_achievement_percentages_for_app(440)
Dict{String, Float16}("TF_MAPS_DOOMSDAY_PUSH_INTO_EXHAUST" => 7.9...)
```
