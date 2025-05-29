```
save_results(results, xlfile, paramsets) → (;dfs)
```

関数 [`save_dfs`](@ref)、[`save_all_plots`](@ref)、[`write_errors`](@ref) を呼び出して、結果とエラーを保存します。

# 引数

  * `results`: 構造 `(; overview, subsets_results, résumé, errors)` を持つ `NamedTuple`
  * `overview`, `subsets_results`, `résumé`::NamedTuple: 実際のデータ処理の結果を (; plots=(;df1, df2...), ...) の形式で。キー 'plots' はオプションです。
  * `xlfile`: パラメータを含む XLSX ファイルへのパス。
  * `paramsets::Vector{NamedTuple}`

# 戻り値

  * `(;dfs)`: [`save_dfs`](@ref) によって返される DataFrames の NamedTuple

関数 `save_results` は公開されており、エクスポートされていません。
