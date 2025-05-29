```
rdb_providers(
    code::Bool = false;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    kwargs...
)
```

`rdb_providers` は [DBnomics](https://db.nomics.world/) からプロバイダーのリストをダウンロードします。

デフォルトでは、この関数は [DBnomics](https://db.nomics.world/) からのプロバイダーのリストを含む `DataFrame` を返し、地域、ウェブサイトなどの追加情報が含まれます。

# 引数

  * `code::Bool = false`: `true` の場合、プロバイダーのみが配列で返されます。
  * `use_readlines::Bool = DBnomics.use_readlines`: (デフォルト `false`) `true` の場合、データは `readlines` 関数を使用して要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: (デフォルト `nothing`) `nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の `HTTP.get` 関数のキーワード引数に渡されます。
  * `kwargs...`: `HTTP.get` に渡されるキーワード引数。

# 例

```jldoctest
julia> rdb_providers()

julia> rdb_providers(true)

julia> rdb_providers(use_readlines = true)

julia> rdb_providers(curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# HTTP.jl の動作に関して、別のオプションを変更する必要があるかもしれません
# これにより、URL が https:// から http:// に変更されます
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
