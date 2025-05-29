```
rdb_datasets(
    provider_code::Union{Nothing, String, Array} = nothing;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    simplify::Bool = false,
    kwargs...
)
```

`rdb_datasets` downloads the list of available datasets for a selection of providers (or all of them) from [DBnomics](https://db.nomics.world/).

By default, the function returns a `Dict` of `DataFrame`s containing the datasets of the providers from [DBnomics](https://db.nomics.world/).

# Arguments

  * `provider_code::Union{Nothing, String, Array} = nothing`: DBnomics code of one or multiple providers. If `nothing`, the providers are firstly dowloaded with the function `rdb_providers` and then the available datasets are requested.
  * `use_readlines::Bool = DBnomics.use_readlines`: (default `false`) If `true`, then the data are requested and read with the function `readlines`.
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (default `nothing`) If not `nothing`, it is used to configure a proxy connection. This configuration is passed to the keyword arguments of the function `HTTP.get` of the package **HTTP.jl**.
  * `simplify::Bool = false`: If `true`, when the datasets are requested for only one provider then a `DataFrame` is returned, not a `Dict` of `DataFrame`s.
  * `kwargs...`: Keyword arguments to be passed to `HTTP.get`.

# Examples

```jldoctest
julia> rdb_datasets("IMF")

julia> rdb_datasets("IMF", simplify = true)

julia> rdb_datasets(["IMF", "BDF"])

julia> using ProgressMeter
julia> rdb_datasets()

julia> rdb_datasets("IMF", use_readlines = true)

julia> rdb_datasets("IMF", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
