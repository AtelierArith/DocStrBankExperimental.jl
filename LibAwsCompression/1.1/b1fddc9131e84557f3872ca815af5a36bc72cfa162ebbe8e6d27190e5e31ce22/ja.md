```
aws_huffman_decode(decoder, to_decode, output)
```

バイトバッファを提供されたシンボル配列にデコードします。

# 引数

  * `decoder`:[in] 使用するデコーダオブジェクト
  * `to_decode`:[in] 読み取るエンコードされたバイトバッファ
  * `output`:[in] デコードされたシンボルを書き込むバッファ。デコーダが成長を許可するように設定されている場合、必要に応じて容量が増加します。

# 戻り値

エンコーディングが成功した場合は AWS*OP*SUCCESS、そうでない場合は AWS*OP*ERR

### プロトタイプ

```c
int aws_huffman_decode( struct aws_huffman_decoder *decoder, struct aws_byte_cursor *to_decode, struct aws_byte_buf *output);
```
