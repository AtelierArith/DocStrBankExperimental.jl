```
get_player_achievements(steamid::Int,appid::Int;l::String)::PlayerAchievements
```

**概要**: `get_player_achievements` は、このユーザーのアチーブメントのリストをアプリ ID に基づいて返します。

# 引数

  * `steamid`: フレンドリストを返すための64ビットSteam ID。
  * `appid`: リクエストしているゲームのID。
  * `l`: 言語。指定された場合、リクエストされた言語のデータを返します。

# 例

```julia-repl
julia> dump(get_player_achievements(76561198309475951,553850;l="japanese"))
SteamWebAPIs.PlayerAchievements
  gameName: String "HELLDIVERS™ 2"
  achievements: Array{SteamWebAPIs.Achievement}((38,))
    1: SteamWebAPIs.Achievement
      apiname: String "1"
      achieved: Bool false
      unlocktime: Nothing nothing
      name: String "ヘルダイブ"
      description: String "難易度がエクストリーム以上のミッションを、誰も死ぬことなく完了する"
    2: SteamWebAPIs.Achievement
      apiname: String "2"
      achieved: Bool false
      unlocktime: Nothing nothing
      name: String "武器はいらない"
      description: String "難易度がハード以上のミッションを、誰一人メインウェポンまたは支援武器を発砲せずに完了する"
    ...
    38: SteamWebAPIs.Achievement
      apiname: String "38"
      achieved: Bool true
      unlocktime: DateTime
        instant: Dates.UTInstant{Millisecond}
          periods: Millisecond
            value: Int64 63846249161000
      name: String "管理民主主義を広めよ"
      description: String "１つのミッション中に敵を150体倒す"
```
