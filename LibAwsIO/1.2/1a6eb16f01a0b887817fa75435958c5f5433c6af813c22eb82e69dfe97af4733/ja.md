```
aws_host_resolver_record_connection_failure(resolver, address)
```

はvtableのrecord*connection*failureを呼び出します。

### プロトタイプ

```c
int aws_host_resolver_record_connection_failure( struct aws_host_resolver *resolver, const struct aws_host_address *address);
```
