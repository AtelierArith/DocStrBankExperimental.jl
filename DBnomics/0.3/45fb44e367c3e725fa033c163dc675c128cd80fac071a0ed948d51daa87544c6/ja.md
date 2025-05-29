```
rdb_datasets(
    provider_code::Union{Nothing, String, Array} = nothing;
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    simplify::Bool = false,
    kwargs...
)
```

`rdb_datasets` は、[DBnomics](https://db.nomics.world/) からプロバイダーの選択（またはすべて）に対して利用可能なデータセットのリストをダウンロードします。

デフォルトでは、この関数は [DBnomics](https://db.nomics.world/) のプロバイダーのデータセットを含む `DataFrame` の `Dict` を返します。

# 引数

  * `provider_code::Union{Nothing, String, Array} = nothing`: 1つまたは複数のプロバイダーのDBnomicsコード。`nothing` の場合、プロバイダーはまず `rdb_providers` 関数でダウンロードされ、その後利用可能なデータセットが要求されます。
  * `use_readlines::Bool = DBnomics.use_readlines`: （デフォルト `false`）`true` の場合、データは `readlines` 関数を使用して要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: （デフォルト `nothing`）`nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の `HTTP.get` 関数のキーワード引数に渡されます。
  * `simplify::Bool = false`: `true` の場合、データセットが1つのプロバイダーのみに要求されるとき、`DataFrame` が返され、`DataFrame` の `Dict` は返されません。
  * `kwargs...`: `HTTP.get` に渡されるキーワード引数。

# 例

```jldoctest
julia> rdb_datasets("IMF")

julia> rdb_datasets("IMF", simplify = true)

julia> rdb_datasets(["IMF", "BDF"])

julia> using ProgressMeter
julia> rdb_datasets()

julia> rdb_datasets("IMF", use_readlines = true)

julia> rdb_datasets("IMF", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# HTTP.jlの動作に関して、別のオプションを変更する必要があるかもしれません
# それにより、urlが https:// から http:// に変更されます
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
