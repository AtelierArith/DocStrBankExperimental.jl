```
aws_profile_collection_new_from_buffer(allocator, buffer, source)
```

Create a new profile collection by parsing text in a buffer. Primarily for testing.

### Prototype

```c
struct aws_profile_collection *aws_profile_collection_new_from_buffer( struct aws_allocator *allocator, const struct aws_byte_buf *buffer, enum aws_profile_source_type source);
```
