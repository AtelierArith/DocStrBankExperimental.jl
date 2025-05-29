```
load_configuration(configuration_file::String)::
        Tuple{BrkgaParams, ExternalControlParams}
```

`configuration_file` からパラメータを読み込み、それらをタプルとして返します。

# 例外

  * `LoadError`: ファイルが無効な設定ファイルである場合、パラメータが欠落している場合、またはパラメータの形式が不正な場合。
