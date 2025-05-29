```
aws_host_resolver_get_host_address_count(resolver, host_name, flags)
```

指定されたホストのアドレスの数を取得します。

### プロトタイプ

```c
size_t aws_host_resolver_get_host_address_count( struct aws_host_resolver *resolver, const struct aws_string *host_name, uint32_t flags);
```
