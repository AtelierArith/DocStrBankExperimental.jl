```
function write_configuration(filename::String, brkga_params::BrkgaParams,
                             external_params::ExternalControlParams)
```

`brkga_params` と `external_params` を `filename` に書き込みます。

# 例外

  * `SystemError`: 設定ファイルを開けない場合。
