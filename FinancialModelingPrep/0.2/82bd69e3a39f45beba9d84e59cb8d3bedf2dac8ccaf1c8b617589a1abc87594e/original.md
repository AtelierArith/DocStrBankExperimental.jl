```
exchange_rates(fmp)
exchange_rates(fmp, symbol)
```

Returns the commodity quote for the specified symbol(s).

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A commodity symbol.

See [Crypto-Quote](https://site.financialmodelingprep.com/developer/docs/#Cryptocurrencies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all fx rates
data = commodity_quote(fmp)

# get the fx rates for EURUSD
data = commodity_quote(fmp, "EURUSD")
```
