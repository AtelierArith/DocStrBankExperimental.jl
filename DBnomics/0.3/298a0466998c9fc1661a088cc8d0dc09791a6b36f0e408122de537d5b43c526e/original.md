```
rdb_providers(
    code::Bool = false;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    kwargs...
)
```

`rdb_providers` downloads the list of providers from [DBnomics](https://db.nomics.world/).

By default, the function returns a `DataFrame` containing the list of providers from [DBnomics](https://db.nomics.world/) with additional informations such as the region, the website, etc.

# Arguments

  * `code::Bool = false`: If `true`, then only the providers are returned in an array.
  * `use_readlines::Bool = DBnomics.use_readlines`: (default `false`) If `true`, then the data are requested and read with the function `readlines`.
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (default `nothing`) If not `nothing`, it is used to configure a proxy connection. This configuration is passed to the keyword arguments of the function `HTTP.get` of the package **HTTP.jl**.
  * `kwargs...`: Keyword arguments to be passed to `HTTP.get`.

# Examples

```jldoctest
julia> rdb_providers()

julia> rdb_providers(true)

julia> rdb_providers(use_readlines = true)

julia> rdb_providers(curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
