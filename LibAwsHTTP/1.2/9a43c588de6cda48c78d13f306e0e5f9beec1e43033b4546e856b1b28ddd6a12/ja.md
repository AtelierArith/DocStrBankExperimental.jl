```
aws_http_alpn_map_init(allocator, map)
```

`struct aws\_string *` を `enum [`aws*http*version`](@ref)` にマッピングする空のハッシュテーブルを初期化します。このマップは aws*http*client*connections*options.alpn*string*map で使用できます。

### プロトタイプ

```c
int aws_http_alpn_map_init(struct aws_allocator *allocator, struct aws_hash_table *map);
```
