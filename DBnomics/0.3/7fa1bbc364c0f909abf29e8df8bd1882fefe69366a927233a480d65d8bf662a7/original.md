```
rdb_dimensions(
    provider_code::Union{Nothing, String, Array} = nothing,
    dataset_code::Union{Nothing, String, Array} = nothing;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    simplify::Bool = false,
    kwargs...
)
```

`rdb_dimensions` downloads the list of dimensions (if they exist) for available datasets of a selection of providers from [DBnomics](https://db.nomics.world/).

By default, the function returns a nested `Dict` of `DataFrame`s containing the dimensions of datasets for providers from [DBnomics](https://db.nomics.world/).

# Arguments

  * `provider_code::Union{Nothing, String, Array} = nothing`: DBnomics code of one or multiple providers. If `nothing`, the providers are firstly dowloaded with the function `rdb_providers` and then the available datasets are requested.
  * `dataset_code::Union{Nothing, String, Array} = nothing`: DBnomics code  of one or multiple datasets of a provider. If `nothing`, the datasets  codes are dowloaded with the function `rdb_datasets` and then  the dimensions are requested.
  * `use_readlines::Bool = DBnomics.use_readlines`: (default `false`) If `true`, then the data are requested and read with the function `readlines`.
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (default `nothing`) If not `nothing`, it is used to configure a proxy connection. This configuration is passed to the keyword arguments of the function `HTTP.get` of the package **HTTP.jl**.
  * `simplify::Bool = false`: If `true`, when the dimensions are requested for only one provider and one dataset then a `Dict` of `DataFrame`s is returned, not a nested `Dict` of `DataFrame`s.
  * `kwargs...`: Keyword arguments to be passed to `HTTP.get`.

# Examples

```jldoctest
julia> rdb_dimensions("IMF", "WEO:2019-10")

julia> rdb_dimensions("IMF", "WEO:2019-10", simplify = true)

julia> rdb_dimensions("IMF")

# It is very long !
julia> using ProgressMeter
julia> rdb_dimensions()

julia> rdb_dimensions("IMF", "WEO:2019-10", use_readlines = true)

julia> rdb_dimensions("IMF", "WEO:2019-10", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
