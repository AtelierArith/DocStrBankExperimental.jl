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

`rdb_series` は、[DBnomics](https://db.nomics.world/) の選択されたプロバイダーの利用可能なデータセットのシリーズのリストをダウンロードします。

この関数は（非常に）長い時間がかかる可能性があることをユーザーに警告します。DBnomicsは、21675のデータセットを取得するために63のプロバイダーからデータを要求しており、合計約7億2000万のシリーズを取得します。

デフォルトでは、この関数は、[DBnomics](https://db.nomics.world/) のプロバイダーのデータセットのシリーズを含むネストされた `Dict` の `DataFrame` を返します。

# 引数

  * `provider_code::Union{Nothing, String, Array} = nothing`: 1つまたは複数のプロバイダーのDBnomicsコード。`nothing` の場合、プロバイダーは最初に `rdb_providers` 関数でダウンロードされ、その後利用可能なデータセットが要求されます。
  * `dataset_code::Union{Nothing, String, Array} = nothing`: 1つまたは複数のプロバイダーのデータセットのDBnomicsコード。`nothing` の場合、データセットコードは `rdb_datasets` 関数でダウンロードされ、その後シリーズが要求されます。
  * `dimensions::Union{Dict, NamedTuple, String, Nothing} = nothing`: 指定されたプロバイダーとデータセットの1つまたは複数の次元のDBnomicsコード。`Dict` または `NamedTuple` の場合、パッケージ **JSON.jl** の `json` 関数が適用されてjsonオブジェクトが生成されます。
  * `query::Union{String, Nothing} = nothing`: プロバイダーのデータセットからシリーズをフィルタリング/選択するためのクエリ。
  * `use_readlines::Bool = DBnomics.use_readlines`: （デフォルト `false`）`true` の場合、データは `readlines` 関数で要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: （デフォルト `nothing`）`nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の `HTTP.get` 関数のキーワード引数に渡されます。
  * `simplify::Bool = false`: `true` の場合、次元が1つのプロバイダーと1つのデータセットのみに要求されると、ネストされた `Dict` の `DataFrame` ではなく、`DataFrame` の `Dict` が返されます。
  * `kwargs...`: `HTTP.get` に渡されるキーワード引数。

# 例

```jldoctest
julia> rdb_series("IMF", "WEO:2019-10")

# 次元を指定して
julia> rdb_series("IMF", "WEO:2019-10", dimensions = Dict(Symbol("weo-country") => "AGO"))
julia> rdb_series("IMF", "WEO:2019-10", dimensions = Dict(Symbol("weo-subject") => "NGDP_RPCH"), simplify = true)

# クエリを使用して
julia> rdb_series("IMF", "WEO:2019-10", query = "ARE")
julia> rdb_series("IMF", ["WEO:2019-10", "WEOAGG:2019-10"], query = "NGDP_RPCH")

julia> using ProgressMeter
julia> rdb_series("IMF", "WEO:2019-10")

julia> rdb_series("IMF", "WEO:2019-10", use_readlines = true)

julia> rdb_series("IMF", "WEO:2019-10", curl_config = Dict(:proxy => "http://<proxy>:<port>"))

# HTTP.jlの動作に関して、他のオプションを変更する必要があるかもしれません
# これにより、urlが https:// から http:// に変更されます
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);
```
