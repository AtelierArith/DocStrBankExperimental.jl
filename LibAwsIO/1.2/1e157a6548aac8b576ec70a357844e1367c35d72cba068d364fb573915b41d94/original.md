```
aws_io_library_init(allocator)
```

Initializes internal datastructures used by aws-c-io. Must be called before using any functionality in aws-c-io.

### Prototype

```c
void aws_io_library_init(struct aws_allocator *allocator);
```
