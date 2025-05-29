```
aws_get_profile_name(allocator, override_name)
```

Computes the profile to use for credentials lookups based on profile resolution rules

### Prototype

```c
struct aws_string *aws_get_profile_name(struct aws_allocator *allocator, const struct aws_byte_cursor *override_name);
```
