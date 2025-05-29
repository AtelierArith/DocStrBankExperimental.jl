```
get_user_stats_for_game(steamid::Int,appid::Int)::PlayerStats
```

**Summary**: `get_user_stats_for_game` returns a list of achievements and stats for this user by app id.

# Arguments

  * `steamid`: 64 bit Steam ID to return friend list for.
  * `appid`: The ID for the game you're requesting.

# Example

```julia-repl
julia> get_user_stats_for_game(76561198309475951,1238810)
SteamWebAPIs.PlayerStats("Battlefield ™ V", ["Achievement_GOSCC_1"...], Dict{String, Real}("stat_4" => 1...))
```
