```
price_quote(fmp, symbol)
```

Returns a JSON table with the price quote for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A financial symbol.

See [Company-Quote](https://site.financialmodelingprep.com/developer/docs/#Company-Quote) for more details.
See [Index-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-majors-indexes-(Dow-Jones%2C-Nasdaq%2C-S&P-500)) for more details.
See [Euronext-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-EuroNext) for more details.
See [TSX-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-TSX) for more details.
See [Crypto-Quote](https://site.financialmodelingprep.com/developer/docs/#Cryptocurrencies) for more details.
See [Forex-Quote](https://site.financialmodelingprep.com/developer/docs/#Forex-(FX)) for more details.
See [Commodity-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-Major-Commodities-(Gold%2C-Silver%2C-Oil)) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price quote for AAPL
data = price_quote(fmp, "AAPL")
```
