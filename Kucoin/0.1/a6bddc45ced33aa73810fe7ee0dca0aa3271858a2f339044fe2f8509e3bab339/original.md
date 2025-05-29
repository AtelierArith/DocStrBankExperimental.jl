```
Kucoin.list_accounts(api_data[; currency[, type]]) -> JSON3.Array{JSON3.Object}
```

Get a list of accounts. See Kucoin official [docs](https://docs.kucoin.com/#list-accounts)  for more details.

# Arguments

  * `api_data::UserApiData`: holds user API data susch as api key, secret, passphrase, etc.

# Keywords

  * `currency::String`: [Optional] a unique currency kucoin code
  * `type::String`: [Optional] an account type, the valid values are: `"main"`, `"trade"`,

`"margin"` or `"pool"`

# Returns

  * `JSON3.Array{JSON3.Object}`

```json
[
  {
    "id": "5bd6e9286d99522a52e458de",  //accountId
    "currency": "BTC",  //Currency
    "type": "main",  //Account type, including main and trade
    "balance": "237582.04299",  //Total assets of a currency
    "available": "237582.032",  //Available assets of a currency
    "holds": "0.01099"  //Hold assets of a currency
  },
  {
    "id": "5bd6e9216d99522a52e458d6",
    "currency": "BTC",
    "type": "trade",
    "balance": "1234356",
    "available": "1234356",
    "holds": "0"
}]
```
