```
ProviderEHRLaunchConfig(; kwargs...)
```

## Required Keyword Arguments:

  * `client_id::String`
  * `redirect_uri::String`

## Optional Keyword Arguments:

  * `enforce_iss_https::Bool`. Default value: `true`
  * `enforce_iss_allowlist::Bool`. Default value: `true`
  * `iss_allowlist::Vector{String}`. Default value: `String[]`
