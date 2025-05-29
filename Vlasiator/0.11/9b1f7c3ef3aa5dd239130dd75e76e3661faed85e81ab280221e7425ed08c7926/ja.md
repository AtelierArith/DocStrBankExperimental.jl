```
readvariable(meta::MetaVLSV, var::String, sorted::Bool=true, usemmap::Bool=false) -> Array
```

`meta` に関連付けられた VLSV ファイルから `var` の変数値を返します。デフォルトでは、DCCRG 変数はセル ID によってソートされます。`usemmap` はメモリマップ IO を使用するかどうかを決定します。これは特に大きな配列に対して便利です。
