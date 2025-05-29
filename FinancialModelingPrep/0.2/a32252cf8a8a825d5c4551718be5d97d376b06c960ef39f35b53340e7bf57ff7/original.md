```
available_crytocurrencies(fmp)
```

Returns all available cryptocurrencies in the API.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Cryptocurrencies-List](https://site.financialmodelingprep.com/developer/docs/#Historical-Cryptocurrencies-Price) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all available cryptocurrencies
data = available_crytocurrencies(fmp)
```
