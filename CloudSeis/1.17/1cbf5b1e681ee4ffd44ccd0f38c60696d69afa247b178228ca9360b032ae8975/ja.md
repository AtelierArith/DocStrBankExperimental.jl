```
trcs,hdrs = readframe(io::CSeis, idx...; regularize=true)
```

`io` からフレーム `idx...` のトレースとヘッダーを読み取ります。 `idx...` は整数または `CartesianIndex` であることができます。

`regularize` という名前の引数は、圧縮方法が `LeftJustifyCompressor` の場合にのみ適用されます。 true に設定すると、トレースは正しいコンテキスト位置に正規化されます。それ以外の場合、トレースは左寄せのままになります。 その後、`regularize!` メソッドを使用することもできます。
