```
aws_huffman_decoder_allow_growth(decoder, allow_growth)
```

デコーディング中に出力バッファが満杯になったときに、容量を増やすかどうかを設定します。デフォルトではfalseです。

### プロトタイプ

```c
void aws_huffman_decoder_allow_growth(struct aws_huffman_decoder *decoder, bool allow_growth);
```
