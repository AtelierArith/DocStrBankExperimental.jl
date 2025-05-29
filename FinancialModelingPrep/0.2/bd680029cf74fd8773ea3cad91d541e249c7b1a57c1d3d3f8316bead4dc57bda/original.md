```
price_quotes(fmp, market)
```

Returns a JSON table with the price quotes for the specified market.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `market::String`: A financial market.

See [Stock-Quote](https://site.financialmodelingprep.com/developer/docs/#Stock-Price) for more details.
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

# get the price quotes for major indexes
data = price_quote(fmp, "index")

# get the price quotes for NYSE
data = price_quote(fmp, "nyse")

# get the price quotes for TSX
data = price_quote(fmp, "euronext")

# get the price quotes for euronext
data = price_quote(fmp, "tsx")

# get the price quotes for crypto
data = price_quote(fmp, "crypto")

# get the price quotes for forex
data = price_quote(fmp, "forex")

# get the price quotes for commodity
data = price_quote(fmp, "commodity")
```
