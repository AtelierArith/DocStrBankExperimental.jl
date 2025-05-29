```
aws_huffman_get_encoded_length(encoder, to_encode)
```

Get the byte length of to_encode post-encoding.

# Arguments

  * `encoder`:[in] The encoder object to use
  * `to_encode`:[in] The symbol buffer to encode

# Returns

The length of the encoded string.

### Prototype

```c
size_t aws_huffman_get_encoded_length(struct aws_huffman_encoder *encoder, struct aws_byte_cursor to_encode);
```
