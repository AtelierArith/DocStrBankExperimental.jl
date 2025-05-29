```
rdb_last_updates(
    all_updates::Bool = false;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    kwargs...
)
```

`rdb_last_updates` downloads informations about the last updates from [DBnomics](https://db.nomics.world/)

By default, the function returns a `DataFrame` containing the last 100 updates from [DBnomics](https://db.nomics.world/) with additional informations.

# Arguments

  * `all_updates::Bool = false`: If `true`, then the full dataset of the last updates is retrieved.
  * `use_readlines::Bool = DBnomics.use_readlines`: (default `false`) If `true`, then the data are requested and read with the function `readlines`.
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (default `nothing`) If not `nothing`, it is used to configure a proxy connection. This configuration is passed to the keyword arguments of the function `HTTP.get` of the package **HTTP.jl**.
  * `kwargs...`: Keyword arguments to be passed to `HTTP.get`.

# Examples

```jldoctest
julia> rdb_last_updates();

julia> rdb_last_updates(true);

julia> rdb_last_updates(use_readlines = true);

julia> rdb_last_updates(curl_config = Dict(:proxy => "http://<proxy>:<port>"));

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
