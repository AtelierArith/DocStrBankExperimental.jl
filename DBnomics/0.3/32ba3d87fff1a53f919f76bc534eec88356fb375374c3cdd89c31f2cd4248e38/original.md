```
rdb_series(
    provider_code::Union{Nothing, String, Array} = nothing,
    dataset_code::Union{Nothing, String, Array} = nothing;
    dimensions::Union{Dict, NamedTuple, String, Nothing} = nothing,
    query::Union{String, Nothing} = nothing,
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    simplify::Bool = false,
    kwargs...
)
```

`rdb_series` downloads the list of series for available datasets of a selection of providers from [DBnomics](https://db.nomics.world/).

We warn the user that this function can be (very) long to execute. We remind that DBnomics requests data from 63 providers to retrieve 21675 datasets for a total of approximately 720 millions series.

By default, the function returns a nested `Dict` of `DataFrame`s containing the series of datasets for providers from [DBnomics](https://db.nomics.world/).

# Arguments

  * `provider_code::Union{Nothing, String, Array} = nothing`: DBnomics code of one or multiple providers. If `nothing`, the providers are firstly dowloaded with the function `rdb_providers` and then the available datasets are requested.
  * `dataset_code::Union{Nothing, String, Array} = nothing`: DBnomics code  of one or multiple datasets of a provider. If `nothing`, the datasets  codes are dowloaded with the function `rdb_datasets` and then  the series are requested.
  * `dimensions::Union{Dict, NamedTuple, String, Nothing} = nothing`: DBnomics code of one or several dimensions in the specified provider and dataset. If it is a `Dict` or a `NamedTuple`, then then function `json` (from the package **JSON.jl**) is applied to generate the json object.
  * `query::Union{String, Nothing} = nothing`: A query to filter/select series from a provider's dataset.
  * `use_readlines::Bool = DBnomics.use_readlines`: (default `false`) If `true`, then the data are requested and read with the function `readlines`.
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (default `nothing`) If not `nothing`, it is used to configure a proxy connection. This configuration is passed to the keyword arguments of the function `HTTP.get` of the package **HTTP.jl**.
  * `simplify::Bool = false`: If `true`, when the dimensions are requested for only one provider and one dataset then a `Dict` of `DataFrame`s is returned, not a nested `Dict` of `DataFrame`s.
  * `kwargs...`: Keyword arguments to be passed to `HTTP.get`.

# Examples

```jldoctest
julia> rdb_series("IMF", "WEO:2019-10")

# With dimensions
julia> rdb_series("IMF", "WEO:2019-10", dimensions = Dict(Symbol("weo-country") => "AGO"))
julia> rdb_series("IMF", "WEO:2019-10", dimensions = Dict(Symbol("weo-subject") => "NGDP_RPCH"), simplify = true)

# With query
julia> rdb_series("IMF", "WEO:2019-10", query = "ARE")
julia> rdb_series("IMF", ["WEO:2019-10", "WEOAGG:2019-10"], query = "NGDP_RPCH")

julia> using ProgressMeter
julia> rdb_series("IMF", "WEO:2019-10")

julia> rdb_series("IMF", "WEO:2019-10", use_readlines = true)

julia> rdb_series("IMF", "WEO:2019-10", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
