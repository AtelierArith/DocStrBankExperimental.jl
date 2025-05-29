```
show_fills(user_data::UserInfo, pair::String)
```

Get a list of recent fills of the API key's profile for a given pair.

# Arguments

  * `user_data::UserInfo` : API data
  * `pair::String` : "ETH-EUR" etc.

# Example

```julia-repl
julia> show_fills(user_data, "ETH-EUR")
7×13 DataFrame
 Row │ created_at                fee                 liquidity  order_id                           price   ⋯
     │ String                    String              String     String                             String  ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-07-04T21:54:09.902Z  0.0746268391200000  T          d275ae2b-4f34-4ce9-98a7-1147bccf…  2003.90 ⋯
   2 │ 2021-07-04T15:43:54.115Z  0.0733968750000000  T          7a019bf8-bee8-4001-bb34-e3d6f3e6…  1957.25
```
