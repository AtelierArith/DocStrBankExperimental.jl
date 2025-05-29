```
PrefectAPI(url::String, key::SecretString) <:AbstractPrefectInterface
PrefectAPI(url::String)
PrefectAPI()
```

Mutable struct tha stores the Prefect server api endpoint. All `PrefectInterface` operations depend on connecting to a running Prefect server to pull block information. Constructor with no arguments assigns env variables `PREFECT_API_URL`, `PREFECT_API_KEY`

If `PREFECT_API_KEY` does not exist then an empty string is assigned to `key`. For Prefect Server with no authentication (or with auth managed by connection string) the empty key will not interfere with API calls.

# Examples:

```jldoctest
julia> using PrefectInterfaces

julia> ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api"; ENV["PREFECT_API_KEY"] = "zyxw4321";

julia> api = PrefectAPI()
PrefectAPI("http://127.0.0.1:4300/api", ####Secret####)

julia> api.url
"http://127.0.0.1:4300/api"

julia> api.key.secret
"zyxw4321"

julia> api.url = "https://api.prefect.cloud/api/accounts/0eEXAMPLE";

julia> api.key = SecretString("abcd1234")
####Secret####

julia> api = PrefectAPI("https://api.prefect.cloud/api/accounts/0eEXAMPLE", "abcd1234")
PrefectAPI("https://api.prefect.cloud/api/accounts/0eEXAMPLE", ####Secret####)
```
