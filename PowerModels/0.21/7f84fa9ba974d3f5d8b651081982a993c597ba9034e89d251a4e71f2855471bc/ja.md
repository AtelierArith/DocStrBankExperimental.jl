```
parse_file(io::String; import_all=false, validate=true)
parse_file(io::IO; import_all=false, validate=true, filetype="json")
```

ファイルをPowerModelsデータ構造に解析します。

サポートされているファイルタイプは次のとおりです：

  * `.m`: Matpowerファイル
  * `.raw`: PTI (PSS(R)E-v33)
  * `.json`: PowerModels.jl JSONファイル

`import_all`がtrueの場合、PTIファイルのすべてのフィールドがインポートされます。

`validate = true`の場合、PowerModelsはインポートされたデータの正確性を検証します。
