```
aws_profile_collection_new_from_file(allocator, file_path, source)
```

Create a new profile collection by parsing a file with the specified path

### Prototype

```c
struct aws_profile_collection *aws_profile_collection_new_from_file( struct aws_allocator *allocator, const struct aws_string *file_path, enum aws_profile_source_type source);
```
