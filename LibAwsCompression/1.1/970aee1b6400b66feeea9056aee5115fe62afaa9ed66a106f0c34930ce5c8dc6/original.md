```
aws_huffman_decoder_allow_growth(decoder, allow_growth)
```

Set whether or not to increase capacity when the output buffer fills up while decoding. This is false by default.

### Prototype

```c
void aws_huffman_decoder_allow_growth(struct aws_huffman_decoder *decoder, bool allow_growth);
```
