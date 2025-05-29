```
aws_default_dns_resolve(allocator, host_name, output_addresses, user_data)
```

警告！この関数を直接呼び出さないでください (getaddrinfo()): ブロックします。他の解決関数のためにこの関数へのポインタを提供してください。

### プロトタイプ

```c
int aws_default_dns_resolve( struct aws_allocator *allocator, const struct aws_string *host_name, struct aws_array_list *output_addresses, void *user_data);
```
