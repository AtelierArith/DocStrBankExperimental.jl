```
insider_trading_types(fmp)
```

Returns insider trading transaction types.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Insider-Trading](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the types of insider trading events
data = insider_trading_types(fmp)
```
