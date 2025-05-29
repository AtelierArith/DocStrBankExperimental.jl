```
Kucoin.cancel_all_orders(api_data[; symbol[, trade_type]]]) -> Union{JSON3.Array{String},JSON3.Array{Union{}}}
```

Cancel all open orders. See Kucoin official  [docs](https://docs.kucoin.com/#cancel-all-orders) for more details.

# Arguments

  * `api_data::UserApiData`: holds user API data susch as api key, secret, passphrase, etc.

# Keywords

  * `symbol::String`: [Optional] a valid symbol code for the trading pair
  * `trade_type::String`: [Optional] the type of trading, cancel the orders for the specified

trading type, and the default is to cancel the spot trading order (`TRADE`)

# Returns

  * `Union{JSON3.Array{String},JSON3.Array{Union{}}}`: a list of ids of the canceled orders

```json
[
  "5c52e11203aa677f33e493fb",  //orderId
  "5c52e12103aa677f33e493fe",
  "5c52e12a03aa677f33e49401",
  "5c626b0803aa676fee8412a2"
]
```
