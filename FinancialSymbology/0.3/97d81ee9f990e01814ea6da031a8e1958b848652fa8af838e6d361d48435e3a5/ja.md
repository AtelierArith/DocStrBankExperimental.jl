```
OpenFigiAPI(protocol::AbstractString="https",
            base::AbstractString="api.openfigi.com",
            version::AbstractString="v3",
            path::AbstractString="mapping";
            headers::Vector{Pair{String, String}}=["Content-Type"=>"application/json"],
            apikey::String="")::OpenFigiAPI
```

OpenFigiAPIを作成します。

参照: [`fetchsecuritydata`](@ref)

# 例

```jldoctest; setup = :(using FinancialSymbology)
julia> OpenFigiAPI()
OpenFigiAPI: https://api.openfigi.com/v3/mapping
```
