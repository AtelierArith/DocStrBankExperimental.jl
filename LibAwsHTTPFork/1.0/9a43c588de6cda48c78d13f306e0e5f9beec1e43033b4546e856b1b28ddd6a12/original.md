```
aws_http_alpn_map_init(allocator, map)
```

Initialize an empty hash-table that maps `struct aws\_string *` to `enum [`aws*http*version`](@ref)`. This map can used in aws_http_client_connections_options.alpn_string_map.

### Prototype

```c
int aws_http_alpn_map_init(struct aws_allocator *allocator, struct aws_hash_table *map);
```
