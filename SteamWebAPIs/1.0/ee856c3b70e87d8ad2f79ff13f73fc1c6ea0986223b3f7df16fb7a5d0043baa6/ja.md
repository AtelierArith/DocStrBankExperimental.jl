```
get_friend_list(steamid::Int)::Dict{Int,DateTime}
```

**概要**: `get_friend_list` は、任意のSteamユーザーの友達のDictを返します。ただし、そのSteamコミュニティプロファイルの可視性が「公開」に設定されている場合に限ります。プロファイルが非公開の場合は、何も返されません。Dictのキーはsteamidで、値は友達になった日付です。

# 引数

  * `steamid`: 友達リストを返すための64ビットSteam ID。

# 例

```julia-repl
julia> get_friend_list(76561198202322924)
friends = Dict(76561198347283942 => Dates.DateTime("2021-12-24T06:08:57")...)
```
