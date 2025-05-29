```
get_owned_games(steamid::Int;
    include_appinfo::Bool=false,
    include_played_free_games::Bool=false)::OwnedGames
```

**概要**: `get_owned_games` は、プレイヤーが所有しているゲームのリストを返し、プロフィールが公開されている場合はプレイ時間情報も含まれます。プライベート、友達のみ、その他のプライバシー設定は、リクエストしているsteamidにリンクされたWebAPIキーを使用している場合を除き、サポートされていません。

# 引数

  * `steamid`: アカウントのSteamID。

# オプションのキーワード

  * `include_appinfo`: 出力にゲーム名とロゴ情報を含めます。デフォルトはappidsのみを返します。
  * `include_played_free_games`: デフォルトでは、Team Fortress 2のような無料ゲームは除外されます（技術的には誰もが所有しているため）。`include*played*free_games`が設定されている場合、プレイヤーがそれらをプレイしたことがある場合に返されます。これはSteamコミュニティのゲームリストと同じ動作です。

# 例

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
