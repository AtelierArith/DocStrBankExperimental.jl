```
info(nms::Union{Nothing, String, Vector{String}} = nothing; 
    by_env=true, listing=nothing, std_lib=false, upgradable=false, disp_rslt=true, ret_rslt=false)
```

共有環境に関する情報を出力または返します。

# 引数

  * `nms`: 情報を返すパッケージまたは環境の名前。環境名は「@」で始まる必要があります。パッケージ名と環境名を1つの配列で同時に提供することはできません。

# キーワード引数

  * `by_env=true`: 結果を `@env => [pkg1, ...]` のようなペアの `Dict` として出力するか、`pkg => [@env1, ...]` として出力するか。返される結果には影響しません（あれば）。
  * `listing=nothing`: このキーワード引数は `nothing`、`:envs`、または `:pkgs` であることができます。これらの2つの `Symbol` のいずれかが提供されると、結果はそれぞれ環境またはパッケージのベクターとして出力されます。この場合、`by_env` は無視されます。返される結果には影響しません（あれば）。
  * `upgradable=false`: true の場合、他のすべてのキーワード引数は無視され、インストールされたバージョンと最新バージョンの間でアップグレード可能なパッケージのみが環境ごとに出力されます。
  * `disp_rslt=true`: 結果を出力するかどうか。
  * `ret_rslt=false`: 関数が何かを返すかどうか。true に設定すると、NamedTuple `(; env_dict, pkg_dict, envs, pkgs, absent)` を返します。最初の2つの要素は、それぞれ環境またはパッケージによってキーワードに対応する `Dict` です。`envs` と `pkgs` はそれぞれの要素のベクターであり、`absent` は `nms` 引数を通じて提供されたが共有環境に含まれていない名前です。返されるデータの環境名は先頭の「@」なしです。

この関数は公開されていますが、**エクスポートされていません**。名前の衝突を避けるためです。

# 例

```julia-repl
julia> ShareAdd.info(["BenchmarkTools", "Chairmarks"])
次のパッケージは共有環境にありません:
    ["Chairmarks"]

見つかったパッケージ/環境:
  @BenchmarkTools
   => ["BenchmarkTools"]
  @Tools
   => ["BenchmarkTools"]

julia> ShareAdd.info(["DataFrames", "CSV"]; by_env=false)
  CSV
   => ["@DataFrames"]
  DataFrames
   => ["@DataFrames"]

julia> ShareAdd.info("StaticArrays"; upgradable=true)
  @StaticArrays
    StaticArrays: 1.9.8 --> 1.9.10   
```
