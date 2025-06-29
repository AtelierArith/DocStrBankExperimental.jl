```
fetchsecuritydata(id::Identifier, api::OpenFigiAPI=OpenFigiAPI(); kwargs...)::StructArray
fetchsecuritydata(ids::Vector{<:Identifier}, api::OpenFigiAPI=OpenFigiAPI(); kwargs...)::Dict{String, StructArray}

fetchsecuritydata(id::AbstractString, idType::AbstractString, api::OpenFigiAPI=OpenFigiAPI(); kwargs...)::StructArray
fetchsecuritydata(ids::Vector{<:AbstractString}, idType::AbstractString, api::OpenFigiAPI=OpenFigiAPI(); kwargs...)::Dict{String, StructArray}
fetchsecuritydata(ids::Vector{<:AbstractString}, idType::Vector{<:AbstractString}, api::OpenFigiAPI=OpenFigiAPI(); kwargs...)::Dict{String, StructArray}
```

Fetch Identifier data from API. The function accepts either `String`s or [`Identifier`](@ref identifier_header)s.

See also: [`makeidentifier`](@ref), [`Identifier`s](@ref identifier_header)

If using a `String` for the identifier you must also pass the identifier type(s).  If all identifiers are of the same type then you can pass a `String`, alternatively a `Vector` the same length as the `Vector` of identifiers.

Do not broadcast this function over a `Vector` of identifiers.  Pass the `Vector` as the `ids` argument. Returns a `Dict` with [`Identifier`](@ref identifier_header) strings as keys.

Keyword arguments are passed to the API query and must be one or more of:

  * `micCode`
  * `currency`
  * `securityType2`
  * `securityType`
  * `stateCode`
  * `exchCode`
  * `marketSecDes`

More information is available on the [OpenFIGI API](https://www.openfigi.com/api#get-v3-mapping-values) website.

If passing a `Vector` to `ids` then each `kwarg` should be either a `String` or a `Vector` of the same length.

See also: [`OpenFigiAPI`](@ref), [`OpenFigiAsset`](@ref)

# Examples

```jldoctest; setup = :(using FinancialSymbology)
julia> identifiers = makeidentifier.(["AAPL US Equity", "BDDXSM4"])
2-element Vector{Identifier}:
 "AAPL US Equity"
 "BDDXSM4"


julia> fetchsecuritydata(identifiers)
Dict{String, StructArrays.StructArray} with 2 entries:
  "AAPL US Equity" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "BDDXSM4"        => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
```

```jldoctest; setup = :(using FinancialSymbology)
julia> identifiers = [Ticker("AAPL US Equity"), Sedol("BDDXSM4")]
2-element Vector{Identifier}:
 "AAPL US Equity"
 "BDDXSM4"


julia> fetchsecuritydata(identifiers)
Dict{String, StructArrays.StructArray} with 2 entries:
  "AAPL US Equity" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "BDDXSM4"        => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
```

```jldoctest; setup = :(using FinancialSymbology)
julia> tickers = ["AAPL", "VOD", "TSLA"]
3-element Vector{String}:
 "AAPL"
 "VOD"
 "TSLA"

julia> fetchsecuritydata(tickers, "TICKER"; marketSecDes="Equity", exchCode=["US", "LN", "US"])
Dict{String, StructArrays.StructArray} with 3 entries:
  "AAPL" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "VOD"  => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "TSLA" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
```

```jldoctest; setup = :(using FinancialSymbology)
julia> idstrings = ["BBG000B9XRY4", "037833100", "US0378331005"]
3-element Vector{String}:
 "BBG000B9XRY4"
 "037833100"
 "US0378331005"

julia> idtypes = ["ID_BB_GLOBAL", "ID_CUSIP", "ID_ISIN"]
3-element Vector{String}:
 "ID_BB_GLOBAL"
 "ID_CUSIP"
 "ID_ISIN"

julia> fetchsecuritydata(idstrings, idtypes; exchCode="US")
Dict{String, StructArrays.StructArray} with 3 entries:
  "US0378331005" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "037833100"    => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
  "BBG000B9XRY4" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…
```
