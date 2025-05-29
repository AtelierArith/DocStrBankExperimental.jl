```
ProviderEHRLaunchConfig(; kwargs...)
```

## 必須のキーワード引数:

  * `client_id::String`
  * `redirect_uri::String`

## 任意のキーワード引数:

  * `enforce_iss_https::Bool`. デフォルト値: `true`
  * `enforce_iss_allowlist::Bool`. デフォルト値: `true`
  * `iss_allowlist::Vector{String}`. デフォルト値: `String[]`
