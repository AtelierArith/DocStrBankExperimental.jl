```
cancel_all_orders(user_data::UserInfo)
```

APIキーに関連付けられたプロファイルからすべてのオープンオーダーをキャンセルします。

# 例

```julia-repl
julia>cancel_all_orders(user_data)
1-element Vector{Any}:
 "35fa8e19-f204-40c0-b995-eb2e4e168e01"
```
