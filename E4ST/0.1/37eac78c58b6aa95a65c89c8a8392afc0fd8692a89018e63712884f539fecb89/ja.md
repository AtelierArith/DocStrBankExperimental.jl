```
process_results!(config::OrderedDict, data::OrderedDict) -> data
```

[`modify_results!(mod, config, data)`](@ref)を`config`内の各`Modification`に対して呼び出します。`config[:save_data_processed]`が`true`（デフォルト）であれば、結果を`get_out_path(config, "data_processed.jls")`に保存します。
