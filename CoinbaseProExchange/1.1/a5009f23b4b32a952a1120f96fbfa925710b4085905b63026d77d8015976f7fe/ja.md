```
cancel_order(order_id::String, user_data::UserInfo)
```

指定された注文IDで注文をキャンセルします。

# 引数

  * `order_id::String` : 注文ID、次の方法で取得できます

`show_open_orders(user_data)`

  * `user_data::UserInfo` : APIデータ

# 例

```julia-repl
julia>cancel_order("5591e17e-5f79-41f0-93d5-b455ec552ecc", user_data)
"5591e17e-5f79-41f0-93d5-b455ec552ecc"
```
