```
company_from_cusip(fmp, cusip)
```

Returns all companies matching the specified cusip.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * cusip::String: A cusip.

See [Cusip-Mapper](https://site.financialmodelingprep.com/developer/docs/#Form-13F) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all companies matching the cusip
data = company_from_cusip(fmp, cusip = "000360206")
```
