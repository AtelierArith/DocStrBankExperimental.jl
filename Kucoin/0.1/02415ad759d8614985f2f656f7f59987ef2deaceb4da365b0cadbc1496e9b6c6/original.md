```
Kucoin.place_market_order(api_data[; <keyword arguments>]]) -> JSON3.Object
```

Place a market order. See Kucoin official [docs](https://docs.kucoin.com/#place-a-new-order)  for more details.

# Arguments

  * `api_data::UserApiData`: holds user API data susch as api key, secret, passphrase, etc.

# Keywords

  * `size::String`: [Optional] desired amount in base currency. It is required that you use

one of the two parameters, `size` or `funds`.

  * `funds::String`: [Optional] the desired amount of quote currency to use. It is required

that you use one of the two parameters, `size` or `funds`.

  * `client_order_id::String`: unique order id created by users to identify their orders,

e.g. UUID

  * `side::String`: `"buy"` or `"sell"`
  * `symbol::String`: a valid trading symbol code. e.g. `"ETH-BTC"`
  * `remark::String`: [Optional] remark for the order, length cannot exceed 100 utf-8

characters

  * `stp::String`: [Optional] self trade prevention, valid values: `"CN"`, `"CO"`, `"CB"`

or `"DC"`, read [Self-Trade Prevention](https://docs.kucoin.com/#self-trade-prevention)

# Returns

  * `JSON3.Object`

```json
{
  "orderId": "5bd6e9286d99522a52e458de"
}
```
