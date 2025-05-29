```
insider_trades(fmp, params...)
```

Returns insider trades.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Insider-Trading](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the most recent insider purchases and sales
data = insider_trades(fmp, transactionType = ["P-Purchase", "S-Sale"], page = 0)

# get the most recent insider trades for AAPL
data = insider_trades(fmp, symbol = "AAPL", page = 0)
```
