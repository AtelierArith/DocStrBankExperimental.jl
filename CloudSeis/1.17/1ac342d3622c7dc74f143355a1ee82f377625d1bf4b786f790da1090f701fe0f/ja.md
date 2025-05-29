```
readframetrcs!(io::CSeis, trcs, idx...[; regularize=true])
```

`io` から `trcs::Matrix` にフレーム `idx...` のトレースを読み込みます。 `idx...` は整数または `CartesianIndex` であることができます。

`regularize` という名前の引数は、圧縮方法が `LeftJustifyCompressor` の場合にのみ適用されます。 true に設定すると、トレースは正しいコンテキスト位置に正規化されます。 そうでない場合、トレースは左寄せのままになります。 その後、`regularize!` メソッドを使用することができます。
