```
show_server_time(time_type::String)
```

APIサーバーの時間を取得します。

# 引数

  * `time_type::String` : "iso"（デフォルト）または "epoch"（Unixエポックからの小数秒を表します）

# 例

```julia-repl
julia> show_server_time("iso")
"2021-07-06T22:09:17.231Z"
```
