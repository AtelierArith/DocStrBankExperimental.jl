```
readframe!(io::CSeis, trcs, hdrs, idx...; regularize=true)
```

`io` から `trcs::Matrix` と `hdrs::Matrix` にトレースとヘッダーをフレーム `idx...` のために読み込みます。 `idx...` は整数または `CartesianIndex` であることができます。

`regularize` という名前付き引数は、圧縮方法が `LeftJustifyCompressor` の場合にのみ適用されます。 true に設定すると、トレースは正しいコンテキスト位置に正規化されます。それ以外の場合、トレースは左寄せのままになります。 その後、`regularize!` メソッドを使用することができます。
