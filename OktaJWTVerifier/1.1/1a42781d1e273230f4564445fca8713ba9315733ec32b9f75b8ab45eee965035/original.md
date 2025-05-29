```
Verifier(issuer::String;
    claims_to_validate::Dict{String, String} = Dict{String, String}(),
    timeout::Dates.Minute = Dates.Minute(5),
    discovery_well_known_url::String = "/.well-known/openid-configuration",
    cache::Cache = Cache{String, Any}(timeout),
    metadata_cache::Cache = Cache{String, Any}(timeout),
    leeway::Int64 = 120,
    cleanup::Dates.Minute = Dates.Minute(5)
)
```

Create a new Verifier for the given issuer. The issuer is the full issuer URL of the Okta org, e.g. https://dev-123456.okta.com/oauth2/default. The issuer is used to fetch the metadata for the Okta org, which is cached for the duration of the timeout.

Verifier objects can then be used to verify access tokens and id tokens. See [`verify_access_token!`](@ref) and [`verify_id_token!`](@ref) for more details.
