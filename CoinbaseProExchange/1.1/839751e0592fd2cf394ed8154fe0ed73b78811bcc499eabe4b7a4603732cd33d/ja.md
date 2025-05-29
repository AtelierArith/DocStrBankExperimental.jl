```
show_fees(user_data::UserInfo)
```

現在のメイカーおよびテイカー手数料率、ならびに30日間のトレーリングボリュームを取得します。

# 引数

  * `user_data::UserInfo` : APIデータ

# 例

```julia-repl
julia> show_fees(user_data_default)
1×3 DataFrame
 Row │ maker_fee_rate  taker_fee_rate  usd_volume 
     │ String          String          String     
─────┼────────────────────────────────────────────
   1 │ 0.0050          0.0050          117.09
```
