```
show_fees(user_data::UserInfo)
```

Get current maker & taker fee rates, as well as your 30-day trailing volume.

# Arguments

  * `user_data::UserInfo` : API data

# Example

```julia-repl
julia> show_fees(user_data_default)
1×3 DataFrame
 Row │ maker_fee_rate  taker_fee_rate  usd_volume 
     │ String          String          String     
─────┼────────────────────────────────────────────
   1 │ 0.0050          0.0050          117.09
```
