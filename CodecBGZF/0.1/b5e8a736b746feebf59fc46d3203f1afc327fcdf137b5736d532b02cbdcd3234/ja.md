```
VirtualOffset(block_offset::Integer, inblock_offset::Integer)
```

`block_offset` と `inblock_offset` から仮想ファイルオフセットを作成します。`offsets(v)` で2つのオフセットを取得します。

`block_offset` は BGZF ファイル内の BGZF ブロックの先頭位置を指すオフセットであり、`inblock_offset` は非圧縮 BGZF ブロック内のバイナリデータの先頭位置を指すオフセットです。これらの値はゼロベースであり、有効な範囲はそれぞれ [0, 1 << 48) と [0, 1 << 16) です。
