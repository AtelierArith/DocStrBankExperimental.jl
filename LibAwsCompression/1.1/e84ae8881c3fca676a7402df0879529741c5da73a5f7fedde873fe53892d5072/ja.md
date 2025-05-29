```
aws_huffman_get_encoded_length(encoder, to_encode)
```

エンコーディング後の to_encode のバイト長を取得します。

# 引数

  * `encoder`:[in] 使用するエンコーダオブジェクト
  * `to_encode`:[in] エンコードするシンボルバッファ

# 戻り値

エンコードされた文字列の長さ。

### プロトタイプ

```c
size_t aws_huffman_get_encoded_length(struct aws_huffman_encoder *encoder, struct aws_byte_cursor to_encode);
```
