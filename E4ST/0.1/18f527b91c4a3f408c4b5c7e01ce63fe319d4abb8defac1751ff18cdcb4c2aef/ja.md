```
modify_model!(mod::DCLine, config, data, model)
```

`data[:dc_lines]` からモデルに dc ラインを追加し、`pflow_dc` 変数を作成し、対応する `pflow_bus` 変数に加算/減算します。
