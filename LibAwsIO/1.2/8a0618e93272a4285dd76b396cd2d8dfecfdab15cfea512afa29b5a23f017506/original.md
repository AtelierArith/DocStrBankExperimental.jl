```
aws_host_resolver_purge_host_cache(resolver, options)
```

Removes the cache for a host asynchronously.

### Prototype

```c
int aws_host_resolver_purge_host_cache( struct aws_host_resolver *resolver, const struct aws_host_resolver_purge_host_options *options);
```
