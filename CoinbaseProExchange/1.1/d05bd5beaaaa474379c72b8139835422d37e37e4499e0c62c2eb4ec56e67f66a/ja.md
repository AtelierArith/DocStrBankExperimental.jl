```
show_exchange_limits(user_data::UserInfo, currency::String)
```

指定された通貨の支払い方法の送金限度額に関する情報を取得します。

# 引数

  * `user_data::UserInfo` : APIデータ
  * `currency::String` : "ETH", "BTC", "XTZ" など。

# 例

```julia-repl
julia> show_exchange_limits(user_data, "ETH")
5×4 DataFrame
 Row │ payment_method     max         period_in_days  remaining  
     │ String             Float64     Int64           Float64    
─────┼───────────────────────────────────────────────────────────
   1 │ ideal_deposit       14.6423                 1   14.6423
   2 │ exchange_withdraw  146.423                  1  146.423
   3 │ secure3d_buy         1.75707                7    1.75707
   4 │ credit_debit_card    0.585691               7    0.585691
   5 │ paypal_withdrawal   11.7138                 1   11.7138
```
