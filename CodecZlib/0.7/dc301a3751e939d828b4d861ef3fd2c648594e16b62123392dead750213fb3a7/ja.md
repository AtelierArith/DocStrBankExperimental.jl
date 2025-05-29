```
GzipDecompressor(;windowbits=15, gziponly=false)
```

gzip デコーダコーデックを作成します。

`gziponly` が `false` の場合、このコーデックは zlib 形式もデコードできます。

## 引数

  * `windowbits` (8..15): `windowbits` をデフォルトの 15 から変更すると、`2^windowbits` より大きな履歴バッファを使用してデータをデコードすることができなくなります。
  * `gziponly`: データ形式検出を無効にするフラグ

!!! warning
    `serialize` と `deepcopy` は、保存された生ポインタのため、このコーデックでは機能しません。

