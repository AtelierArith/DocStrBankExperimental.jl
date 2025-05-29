```
aws_huffman_decode(decoder, to_decode, output)
```

Decodes a byte buffer into the provided symbol array.

# Arguments

  * `decoder`:[in] The decoder object to use
  * `to_decode`:[in] The encoded byte buffer to read from
  * `output`:[in] The buffer to write decoded symbols to. If decoder is set to allow growth, capacity will be increased when necessary.

# Returns

AWS_OP_SUCCESS if encoding is successful, AWS_OP_ERR otherwise

### Prototype

```c
int aws_huffman_decode( struct aws_huffman_decoder *decoder, struct aws_byte_cursor *to_decode, struct aws_byte_buf *output);
```
