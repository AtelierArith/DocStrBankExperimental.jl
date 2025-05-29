```
esg_score_benchmarks(fmp, year)
```

Returns a JSON table with the ESG score benchmarks for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `year::Integer`: A calendar year.

See [ESG-Benchmarking](https://site.financialmodelingprep.com/developer/docs/#ESG-Benchmarking-By-Sector-and-Year) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the esg score benchmarks for 2023
data = esg_score_benchmarks(fmp, year = 2023)
```
