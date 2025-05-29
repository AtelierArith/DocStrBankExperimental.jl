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

指定された発行者の新しい Verifier を作成します。発行者は Okta 組織の完全な発行者 URL であり、例として https://dev-123456.okta.com/oauth2/default があります。発行者は Okta 組織のメタデータを取得するために使用され、タイムアウトの期間中キャッシュされます。

Verifier オブジェクトは、アクセストークンと ID トークンを検証するために使用できます。詳細については、[`verify_access_token!`](@ref) および [`verify_id_token!`](@ref) を参照してください。
