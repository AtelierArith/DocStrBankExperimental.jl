```
aws_get_credentials_file_path(allocator, override_path)
```

Computes the final platform-specific path for the profile credentials file. Does limited home directory expansion/resolution.

override_path, if not null, will be searched first instead of using the standard home directory config path

### Prototype

```c
struct aws_string *aws_get_credentials_file_path( struct aws_allocator *allocator, const struct aws_byte_cursor *override_path);
```
