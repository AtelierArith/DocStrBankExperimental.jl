```
get_owned_games(steamid::Int;
    include_appinfo::Bool=false,
    include_played_free_games::Bool=false)::OwnedGames
```

**Summary**: `get_owned_games` returns a list of games a player owns along with some playtime information, if the profile is publicly visible. Private, friends-only, and other privacy settings are not supported unless you are asking for your own personal details (ie the WebAPI key you are using is linked to the steamid you are requesting).

# Arguments

  * `steamid`: The SteamID of the account.

# Optional keywords

  * `include_appinfo`: Include game name and logo information in the output. The default is to return appids only.
  * `include_played_free_games`: By default, free games like Team Fortress 2 are excluded (as technically everyone owns them). If include*played*free_games is set, they will be returned if the player has played them at some point. This is the same behavior as the games list on the Steam Community.

# Example

```julia-repl
julia> dump(recent_games = get_recently_played_games(76561198202322923,count=1))
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
