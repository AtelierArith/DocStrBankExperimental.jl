```
process_results!(config; processed=true) -> data
```

これは `data` を読み込み、その後 [`process_results!(config, data)`](@ref) を呼び出します。

  * `processed=false` - [`read_parsed_results`](@ref) を介して `data` を読み込みます
  * `processed=true` - [`read_processed_results`](@ref) を介して `data` を読み込みます
