```
OpenFigiAPI(protocol::AbstractString="https",
            base::AbstractString="api.openfigi.com",
            version::AbstractString="v3",
            path::AbstractString="mapping";
            headers::Vector{Pair{String, String}}=["Content-Type"=>"application/json"],
            apikey::String="")::OpenFigiAPI
```

Create OpenFigiAPI.

See also: [`fetchsecuritydata`](@ref)

# Example

```jldoctest; setup = :(using FinancialSymbology)
julia> OpenFigiAPI()
OpenFigiAPI: https://api.openfigi.com/v3/mapping
```
