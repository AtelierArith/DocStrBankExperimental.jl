```
equity_offerings_search(fmp, name)
```

Returns equity offering dates for the specified name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: A company name.

See [Equity-Offerings-Fundraising-Company-Search](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-Company-Search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the equity offering dates for Marinalife
data = equity_offerings_search(fmp, name = "Marinalife")
```
