```
aws_huffman_encode(encoder, to_encode, output)
```

Encode a symbol buffer into the output buffer.

# Arguments

  * `encoder`:[in] The encoder object to use
  * `to_encode`:[in] The symbol buffer to encode
  * `output`:[in] The buffer to write encoded bytes to

# Returns

AWS_OP_SUCCESS if encoding is successful, AWS_OP_ERR otherwise

### Prototype

```c
int aws_huffman_encode( struct aws_huffman_encoder *encoder, struct aws_byte_cursor *to_encode, struct aws_byte_buf *output);
```
