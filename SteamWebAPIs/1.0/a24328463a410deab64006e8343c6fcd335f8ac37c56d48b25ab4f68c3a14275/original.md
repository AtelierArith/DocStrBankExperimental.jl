```
get_recently_played_games(steamid::Int;count=1)::RecentGames
```

**Summary**: `get_recently_played_games` returns a list of games a player has played in the last two weeks, if the profile is publicly visible. Private, friends-only, and other privacy settings are not supported unless you are asking for your own personal details (ie the WebAPI key you are using is linked to the steamid you are requesting).

# Arguments

  * `steamid`: The SteamID of the account.

# Optional keywords

  * `count`: Optionally limit to a certain number of games (the number of games a person has played in the last 2 weeks is typically very small)

# Example

```julia-repl
julia> dump(get_recently_played_games(76561198309475951,count=1))
SteamWebAPIs.RecentGames
  total_count: Int64 5
  games: Array{SteamWebAPIs.RecentGame}((1,))
    1: SteamWebAPIs.RecentGame
      appid: Int64 359550
      name: String "Tom Clancy's Rainbow Six Siege"
      playtime_2weeks: Int64 811
      playtime_forever: Int64 60942
      img_icon_url: String "624745d333ac54aedb1ee911013e2edb7722550e"
```
