executive*compensation*benchmarks(fmp, year)

Returns executive compensation benchmarks for the specified year.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `year::Integer`: A calendar year.

See [Executive-Compensation](https://site.financialmodelingprep.com/developer/docs/#Executive-Compensation) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the excecutive compensation benchmarks for 2020
data = executive_compensation_benchmarks(fmp, year = 2020)
```
