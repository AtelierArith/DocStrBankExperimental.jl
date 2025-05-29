```
aws_huffman_encode(encoder, to_encode, output)
```

シンボルバッファを出力バッファにエンコードします。

# 引数

  * `encoder`:[in] 使用するエンコーダオブジェクト
  * `to_encode`:[in] エンコードするシンボルバッファ
  * `output`:[in] エンコードされたバイトを書き込むバッファ

# 戻り値

エンコードが成功した場合は AWS*OP*SUCCESS、そうでない場合は AWS*OP*ERR

### プロトタイプ

```c
int aws_huffman_encode( struct aws_huffman_encoder *encoder, struct aws_byte_cursor *to_encode, struct aws_byte_buf *output);
```
