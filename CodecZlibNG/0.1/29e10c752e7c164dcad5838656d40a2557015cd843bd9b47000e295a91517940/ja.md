```
GzipDecompressor(;windowbits=15, gziponly=false)
```

gzip デコーダーコーデックを作成します。

`gziponly` が `false` の場合、このコーデックは zlib 形式もデコードできます。

## 引数

  * `windowbits`: ヒストリーバッファのサイズ (8..15)
  * `gziponly`: データ形式検出を無効にするフラグ
