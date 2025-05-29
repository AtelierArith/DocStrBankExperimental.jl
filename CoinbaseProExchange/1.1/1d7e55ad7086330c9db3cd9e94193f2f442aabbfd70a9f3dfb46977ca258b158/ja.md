```
show_transfers(user_data::UserInfo, deposit_type::String="deposit")
```

APIキーのプロフィールから、作成時間の降順で入金/出金のリストを取得します。

# 引数

  * `user_data::UserInfo` : APIデータ
  * `deposit_type::String` : "deposit"（デフォルト）、"internal*deposit"（ポートフォリオ間の転送）、"withdraw"または"internal*withdraw"

# 例

```julia-repl
julia> show_transfers(user_data, "internal_deposit")
4×7 DataFrame
 Row │ account_id                         amount                created_at                     curren ⋯
     │ String                             String                String                         String ⋯
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 6defb94d-80e3-45b4-a6bf-0420cc5f…  10.0000000000000000   2021-07-16 11:10:10.253255+00  EUR    ⋯
   2 │ 6defb94d-80e3-45b4-a6bf-0420cc5f…  10.0000000000000000   2021-07-16 11:07:48.003446+00  EUR
```
