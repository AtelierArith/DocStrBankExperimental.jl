```
function write_configuration(filename::String, brkga_data::BrkgaData,
                             external_params::ExternalControlParams =
                                                    ExternalControlParams())
```

`brkga_data.params` と `external_params` のパラメータを `filename` に書き込みます。

# 例外

  * `SystemError`: 設定ファイルを開けない場合。
