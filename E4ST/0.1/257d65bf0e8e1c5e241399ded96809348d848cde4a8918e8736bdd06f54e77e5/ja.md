```
process_results!(mod_file::String, out_path::String; processed=true) -> data
```

`mod_file`に見つかった[`Modification`](@ref)の結果を処理します。これは、`config`ファイルに似た.ymlファイルです（[`read_config`](@ref]を参照）。`mods`フィールドのみが必要です。

  * `processed=false` - [`read_parsed_results`](@ref)を介して`data`を読み込みます
  * `processed=true` - [`read_processed_results`](@ref)を介して`data`を読み込みます
