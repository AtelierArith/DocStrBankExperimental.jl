```
aws_host_resolver_record_connection_failure(resolver, address)
```

calls record_connection_failure on the vtable.

### Prototype

```c
int aws_host_resolver_record_connection_failure( struct aws_host_resolver *resolver, const struct aws_host_address *address);
```
