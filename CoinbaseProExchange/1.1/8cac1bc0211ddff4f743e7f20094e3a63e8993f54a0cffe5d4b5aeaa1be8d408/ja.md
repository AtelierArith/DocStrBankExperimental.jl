```
show_single_order(order_ID::String, user_data::UserInfo)
```

指定された注文IDの注文情報を取得します。

# 引数

  * `order_id::String` : 注文ID、次の方法で取得できます

`show_open_orders(user_data)`

  * `user_data::UserInfo` : APIデータ

# 例

```julia-repl
julia> show_single_order("14c0db51-ca17-4a8d-9d2c-aa633e703358", user_data)
1×15 DataFrame
 Row │ created_at                 executed_value      fill_fees           filled_size  id                              ⋯
     │ String                     String              String              String       String                          ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-07-04T23:11:02.0001Z  0.0000000000000000  0.0000000000000000  0.00000000   14c0db51-ca17-4a8d-9d2c-aa633e7 ⋯
                                                                                                      11 columns omitted
```
