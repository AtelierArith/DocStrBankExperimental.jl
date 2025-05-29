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

`rdb_dimensions` は、[DBnomics](https://db.nomics.world/) の選択されたプロバイダーの利用可能なデータセットの次元のリストをダウンロードします（存在する場合）。

デフォルトでは、この関数は、[DBnomics](https://db.nomics.world/) のプロバイダーのデータセットの次元を含む `DataFrame` のネストされた `Dict` を返します。

# 引数

  * `provider_code::Union{Nothing, String, Array} = nothing`: 1つまたは複数のプロバイダーのDBnomicsコード。`nothing` の場合、プロバイダーは最初に `rdb_providers` 関数でダウンロードされ、その後利用可能なデータセットが要求されます。
  * `dataset_code::Union{Nothing, String, Array} = nothing`: プロバイダーの1つまたは複数のデータセットのDBnomicsコード。`nothing` の場合、データセットコードは `rdb_datasets` 関数でダウンロードされ、その後次元が要求されます。
  * `use_readlines::Bool = DBnomics.use_readlines`: （デフォルト `false`）`true` の場合、データは `readlines` 関数で要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: （デフォルト `nothing`）`nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の `HTTP.get` 関数のキーワード引数に渡されます。
  * `simplify::Bool = false`: `true` の場合、1つのプロバイダーと1つのデータセットの次元が要求されると、ネストされた `Dict` の `DataFrame` ではなく、`DataFrame` の `Dict` が返されます。
  * `kwargs...`: `HTTP.get` に渡されるキーワード引数。

# 例

```jldoctest
julia> rdb_dimensions("IMF", "WEO:2019-10")

julia> rdb_dimensions("IMF", "WEO:2019-10", simplify = true)

julia> rdb_dimensions("IMF")

# とても長いです！
julia> using ProgressMeter
julia> rdb_dimensions()

julia> rdb_dimensions("IMF", "WEO:2019-10", use_readlines = true)

julia> rdb_dimensions("IMF", "WEO:2019-10", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# HTTP.jl の動作に関して、別のオプションを変更する必要があるかもしれません
# それにより、URLが https:// から http:// に変更されます
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
