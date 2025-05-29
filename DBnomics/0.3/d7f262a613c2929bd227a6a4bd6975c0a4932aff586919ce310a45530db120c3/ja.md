```
rdb_last_updates(
    all_updates::Bool = false;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    kwargs...
)
```

`rdb_last_updates` は [DBnomics](https://db.nomics.world/) からの最新の更新情報をダウンロードします。

デフォルトでは、この関数は [DBnomics](https://db.nomics.world/) からの最新の100件の更新を含む `DataFrame` を返します。

# 引数

  * `all_updates::Bool = false`: `true` の場合、最新の更新の完全なデータセットが取得されます。
  * `use_readlines::Bool = DBnomics.use_readlines`: (デフォルト `false`) `true` の場合、データは `readlines` 関数を使用して要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (デフォルト `nothing`) `nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の `HTTP.get` 関数のキーワード引数に渡されます。
  * `kwargs...`: `HTTP.get` に渡されるキーワード引数。

# 例

```jldoctest
julia> rdb_last_updates();

julia> rdb_last_updates(true);

julia> rdb_last_updates(use_readlines = true);

julia> rdb_last_updates(curl_config = Dict(:proxy => "http://<proxy>:<port>"));

# HTTP.jl の動作に関して、別のオプションを変更する必要があるかもしれません
# これにより、url が https:// から http:// に変更されます
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
