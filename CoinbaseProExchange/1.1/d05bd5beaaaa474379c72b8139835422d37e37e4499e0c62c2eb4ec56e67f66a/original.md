```
show_exchange_limits(user_data::UserInfo, currency::String)
```

Fetch information on the payment method transfer limit for a given currency.

# Arguments

  * `user_data::UserInfo` : API data
  * `currency::String` : "ETH, "BTC", "XTZ" etc.

# Example

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
