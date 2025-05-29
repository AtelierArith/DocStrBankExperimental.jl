```
FMP(apikey, baseurl, headers)
```

Creates a Financial Modeling Prep instance for interacting with the API server endpoints.

# Arguments

  * `apikey::String` = `"demo"`
  * `baseurl::String` = `"https://financialmodelingprep.com"`
  * `headers::Dict{String, String}` = `Dict("Upgrade-Insecure-Requests" => "1")`

# Examples

```julia
# load your FMP API key
FMP_API_KEY = ENV("FMP_API_KEY")

# create a new FMP instance, passing the API key by name
fmp = FMP(apikey = FMP_API_KEY)
```
