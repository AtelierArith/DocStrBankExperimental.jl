```
aws_compression_library_init(alloc)
```

Initializes internal datastructures used by aws-c-compression. Must be called before using any functionality in aws-c-compression.

### Prototype

```c
void aws_compression_library_init(struct aws_allocator *alloc);
```
