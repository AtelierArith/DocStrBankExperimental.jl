```
get_user_stats_for_game(steamid::Int,appid::Int)::PlayerStats
```

**概要**: `get_user_stats_for_game` は、アプリ ID によってこのユーザーの実績と統計のリストを返します。

# 引数

  * `steamid`: フレンドリストを返すための64ビットSteam ID。
  * `appid`: リクエストしているゲームのID。

# 例

```julia-repl
julia> get_user_stats_for_game(76561198309475951,1238810)
SteamWebAPIs.PlayerStats("Battlefield ™ V", ["Achievement_GOSCC_1"...], Dict{String, Real}("stat_4" => 1...))
```
