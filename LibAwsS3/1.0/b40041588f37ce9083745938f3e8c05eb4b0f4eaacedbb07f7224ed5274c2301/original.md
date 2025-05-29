```
aws_s3_library_init(allocator)
```

Initializes internal datastructures used by aws-c-s3. Must be called before using any functionality in aws-c-s3.

### Prototype

```c
void aws_s3_library_init(struct aws_allocator *allocator);
```
