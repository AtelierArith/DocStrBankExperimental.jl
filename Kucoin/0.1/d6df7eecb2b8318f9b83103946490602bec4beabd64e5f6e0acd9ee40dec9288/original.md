```
Kucoin.get_trade_fees(api_data; symbols) -> JSON3.Array{JSON3.Object}
```

Get the actual fee rate of the trading pair. See Kucoin official  [docs](https://docs.kucoin.com/#actual-fee-rate-of-the-trading-pair) for more details.

# Arguments

  * `api_data::UserApiData`: holds user API data susch as api key, secret, passphrase, etc.
  * `symbols::AbstractVector{String}`: Trading pairs (optional, you can inquire fee rates of

10 trading pairs each time at most)

# Returns

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "symbol": "BTC-USDT",
    "takerFeeRate": "0.001",
    "makerFeeRate": "0.001"
  },
  {
    "symbol": "KCS-USDT",
    "takerFeeRate": "0.002",
    "makerFeeRate": "0.0005"
}
```
