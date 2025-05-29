```
show_transfers(user_data::UserInfo, deposit_type::String="deposit")
```

Get a list of deposits/withdrawals from the profile of the API key, in descending order by created time.

# Arguments

  * `user_data::UserInfo` : API data
  * `deposit_type::String` : "deposit" (default), "internal*deposit" (transfer between portfolios), "withdraw" or "internal*withdraw"

# Example

```julia-repl
julia> show_transfers(user_data, "internal_deposit")
4×7 DataFrame
 Row │ account_id                         amount                created_at                     curren ⋯
     │ String                             String                String                         String ⋯
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 6defb94d-80e3-45b4-a6bf-0420cc5f…  10.0000000000000000   2021-07-16 11:10:10.253255+00  EUR    ⋯
   2 │ 6defb94d-80e3-45b4-a6bf-0420cc5f…  10.0000000000000000   2021-07-16 11:07:48.003446+00  EUR
```
