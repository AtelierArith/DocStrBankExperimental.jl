```
aws_host_resolver_resolve_host(resolver, host_name, res, config, user_data)
```

calls resolve_host on the vtable. config will be copied.

### Prototype

```c
int aws_host_resolver_resolve_host( struct aws_host_resolver *resolver, const struct aws_string *host_name, aws_on_host_resolved_result_fn *res, const struct aws_host_resolution_config *config, void *user_data);
```
