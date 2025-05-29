```
XzCompressor(;level=6, check=LZMA_CHECK_CRC64)
```

xz圧縮コーデックを作成します。

## 引数

  * `level`: 圧縮レベル (0..9)
  * `check`: 整合性チェックタイプ (`LZMA_CHECK_{NONE,CRC32,CRC64,SHA256}`)
