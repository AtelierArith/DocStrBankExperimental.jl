```
get_recently_played_games(steamid::Int;count=1)::RecentGames
```

**概要**: `get_recently_played_games` は、プレイヤーが過去2週間にプレイしたゲームのリストを返します。プロファイルが公開されている場合に限ります。プライベート、友達のみ、その他のプライバシー設定は、リクエストしているsteamidにリンクされたWebAPIキーを使用している場合を除き、サポートされていません。

# 引数

  * `steamid`: アカウントのSteamID。

# オプションのキーワード

  * `count`: オプションで特定のゲーム数に制限します（通常、過去2週間にプレイしたゲームの数は非常に少ないです）。

# 例

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
