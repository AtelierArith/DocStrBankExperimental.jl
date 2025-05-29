```
get_player_summaries(steamids::Vector{Int})::Vector{Player}
```

**概要**: `get_player_summaries` は、64ビットのSteam IDのリストに対する基本的なプロフィール情報を返します。

# 引数

  * `steamids`: プロフィール情報を返すための64ビットのSteam IDのベクター。最大100のSteam IDをリクエストできます。

# 例

```julia-repl
julia> dump(get_player_summaries([76561198202322924]))
Array{SteamWebAPIs.Player}((1,))
  1: SteamWebAPIs.Player
    steamid: Int64 76561198309475951
    communityvisibilitystate: Int64 3
    profilestate: Int64 1
    personaname: String "SkyEast"
    profileurl: String "https://steamcommunity.com/id/skyeast/"
    avatar: String "https://avatars.steamstatic.com/de7aed4299406a52b01b0fc087ec5eb1d380b7e7.jpg"
    avatarmedium: String "https://avatars.steamstatic.com/de7aed4299406a52b01b0fc087ec5eb1d380b7e7_medium.jpg"
    avatarfull: String "https://avatars.steamstatic.com/de7aed4299406a52b01b0fc087ec5eb1d380b7e7_full.jpg"
    avatarhash: String "de7aed4299406a52b01b0fc087ec5eb1d380b7e7"
    lastlogoff: DateTime
      instant: Dates.UTInstant{Millisecond}
        periods: Millisecond
          value: Int64 63850008696000
    personastate: Int64 1
    primaryclanid: Int64 103582791455934525
    timecreated: DateTime
      instant: Dates.UTInstant{Millisecond}
        periods: Millisecond
          value: Int64 63601217062000
    personastateflags: Int64 0
    loccountrycode: String "CN"
    locstatecode: Nothing nothing
    loccityid: Nothing nothing
    realname: String "E-Ject"
    gameextrainfo: String "HELLDIVERS™ 2"
    gameid: Int64 553850
```
