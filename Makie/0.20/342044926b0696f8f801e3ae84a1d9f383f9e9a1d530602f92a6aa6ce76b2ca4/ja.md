```
convert_arguments(P, Matrix)::Tuple{ClosedInterval, ClosedInterval, ClosedInterval, Matrix}
```

配列 `{T, 3} where T` を受け取り、次元 `n`、`m`、`k` を `ClosedInterval` に変換し、`ClosedInterval` を `n`、`m`、`k` に格納し、元の配列をタプルに保存します。

`P` はプロットタイプ（オプションです）。
