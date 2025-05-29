```
aws_http_alpn_map_init_copy(allocator, dest, src)
```

Initialize an map copied from the *src map, which maps `struct aws\_string *` to `enum [`aws*http*version`](@ref)`.

### Prototype

```c
int aws_http_alpn_map_init_copy( struct aws_allocator *allocator, struct aws_hash_table *dest, struct aws_hash_table *src);
```
