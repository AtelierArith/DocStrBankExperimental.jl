```
Kucoin.place_limit_order(api_data[; <keyword arguments>]) -> JSON3.Object
```

Place a limit order. See Kucoin official [docs](https://docs.kucoin.com/#place-a-new-order)  for more details.

# Arguments

  * `api_data::UserApiData`: holds user API data susch as api key, secret, passphrase, etc.

# Keywords

  * `price::String`: price per base currency in quote cuurency
  * `size::String`: amount of base currency to buy or sell
  * `time_in_force::String`: [Optional] `"GTC"`, `"GTT"`, `"IOC"`, or `"FOK"` (default is

`"GTC"`), read [Time In Force](https://docs.kucoin.com/#time-in-force)

  * `cancel_after::Int64`: [Optional] cancel after `n` seconds, requires `time_in_force` to

be `"GTT"`

  * `post_only::Bool`: [Optional] post only flag, invalid when `time_in_force` is

`"IOC"` or `"FOK"`, read [Post Only](https://docs.kucoin.com/#post-only)

  * `hidden::Bool`: [Optional] order will not be displayed in the order book
  * `iceberg::Bool`: [Optional] only aportion of the order is displayed in the order book
  * `visible_size::String`: [Optional] the maximum visible size of an iceberg order
  * `client_order_id::String`: unique order id created by users to identify their orders,

e.g. UUID

  * `side::String`: `"buy"` or `"sell"`
  * `symbol::String`: a valid trading symbol code. e.g. `"ETH-BTC"`
  * `remark::String`: [Optional] remark for the order, length cannot exceed 100 utf-8

characters

  * `stp::String`: [Optional] self trade prevention, valid values: `"CN"`, `"CO"`, `"CB"`

or `"DC"`, read [Self-Trade Prevention](https://docs.kucoin.com/#self-trade-prevention)

  * `trade_type::String`: [Optional] the type of trading `TRADE` (Spot Trade), `MARGIN_TRADE`

(Margin Trade). Default is `TRADE`

# Returns

  * `JSON3.Object`

```json
{
  "orderId": "5bd6e9286d99522a52e458de"
}
```
