```
show_open_orders(user_data::UserInfo)
```

指定されたAPIキーに関連付けられたオープンオーダーのリストを取得します。

# 例

```julia-repl
julia> show_open_orders(user_data)
1×15 DataFrame
 Row │ created_at                   executed_value      fill_fees           filled_size  id                            ⋯
     │ String                       String              String              String       String                        ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-07-04T22:15:03.793256Z  0.0000000000000000  0.0000000000000000  0.00000000   5591e17e-5f79-41f0-93d5-b455e ⋯
                                                                                                      11 columns omitted
```
