```
ZeroTemplate
```

すべてのチャンクが `0x00` に等しいバイトで構成される AbstractBinaryTemplate。

# フィールド

  * `expected_file_size::Int`: ファイルの期待サイズ
  * `offsets::Vector{Int}`: 各チャンクのバイトオフセット
  * `chunks_lengths::Vector{Int}`: 各チャンクの長さ
