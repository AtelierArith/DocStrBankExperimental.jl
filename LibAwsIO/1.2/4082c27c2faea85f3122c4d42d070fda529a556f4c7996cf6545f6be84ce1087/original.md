```
aws_host_resolver_get_host_address_count(resolver, host_name, flags)
```

get number of addresses for a given host.

### Prototype

```c
size_t aws_host_resolver_get_host_address_count( struct aws_host_resolver *resolver, const struct aws_string *host_name, uint32_t flags);
```
