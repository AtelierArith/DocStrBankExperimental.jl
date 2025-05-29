```
aws_http_alpn_map_init_copy(allocator, dest, src)
```

*src マップからコピーされたマップを初期化します。このマップは `struct aws\_string *` を `enum [`aws*http*version`](@ref)` にマッピングします。

### プロトタイプ

```c
int aws_http_alpn_map_init_copy( struct aws_allocator *allocator, struct aws_hash_table *dest, struct aws_hash_table *src);
```
