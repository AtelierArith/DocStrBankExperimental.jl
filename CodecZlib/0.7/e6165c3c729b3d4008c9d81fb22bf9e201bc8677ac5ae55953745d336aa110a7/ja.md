```
ZlibDecompressor(;windowbits=15)
```

zlib デコーディングコーデックを作成します。

## 引数

  * `windowbits` (8..15): `windowbits` をデフォルトの 15 から変更すると、`2^windowbits` より大きい履歴バッファを使用してデータをデコードすることができなくなります。

!!! warning
    `serialize` と `deepcopy` は、保存された生ポインタのため、このコーデックでは機能しません。

