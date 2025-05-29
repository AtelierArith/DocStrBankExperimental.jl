```
バイナリテンプレート
```

さまざまなファイルオフセットでの複数のチャンクを持つ一般的なバイナリテンプレート。

# フィールド

  * `expected_file_size::Int`: 期待されるファイルサイズ
  * `offsets::Vector{Int}`: 各チャンクのバイトオフセット
  * `chunks::Vector{Vector{UInt8}}`: 各チャンクのバイト
