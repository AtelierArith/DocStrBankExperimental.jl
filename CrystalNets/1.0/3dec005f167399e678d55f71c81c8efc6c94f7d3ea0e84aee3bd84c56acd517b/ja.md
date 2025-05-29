```
parse_cgd(path::AbstractString; strict=true)
```

.cgd Systre 設定データファイルを解析します。これは RCSR で使用されるものです。`id => g` のリストを返します。ここで `id` は構造の名前で、`g` はその `PeriodicGraph` です。

`strict` が設定されている場合、エラーがあると思われる構造（接続の不整合、セルの欠如、頂点の数が不正確）を拒否し、代わりに `@error` を出力します。
