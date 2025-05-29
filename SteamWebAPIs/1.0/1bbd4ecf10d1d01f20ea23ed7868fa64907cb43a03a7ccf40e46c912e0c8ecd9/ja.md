```
get_number_of_current_players(appid::Int)::Int
```

**概要**: `get_number_of_current_players` は、appid による現在のプレイヤー数を返します。

# 引数

  * `appid`: リクエストしているゲームの ID。

# 例

```julia-repl
julia> get_number_of_current_players(440)
70000
```
