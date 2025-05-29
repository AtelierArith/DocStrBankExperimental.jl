```
show_account_info(user_data::UserInfo, currency::String, info_type::String)
```

与えられたAPIキーに関連付けられた単一の暗号通貨のアカウント情報を取得します。

# 引数

  * `user_data::UserInfo` : APIデータ
  * `currency::String` : 1つ選択、例えば ["ETH"]
  * `info_type::String` : "info"、"history"、または "holds" のいずれかを選択

# 例

```julia-repl
julia> show_account_info(user_data, "ETH", "history")
2×8 DataFrame
 Row │ amount               balance             created_at                   order_id                           produc ⋯
     │ String               String              String                       String                             String ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ -0.0248430100000000  0.0000000000000000  2021-05-09T00:56:06.877638Z  561bd042-9bd8-412f-a905-2a231e77…  ETH-EU ⋯
   2 │ 0.0248430100000000   0.0248430100000000  2021-05-08T23:52:37.666196Z  496f1b74-5a66-45dd-9f6e-817da994…  ETH-EU
                                                                                                       4 columns omitted
```
