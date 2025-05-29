```
aws_host_resolver_purge_cache(resolver)
```

!!! compat "Deprecated"
    Use purge_cache_with_callback instead calls purge_cache on the vtable.


### Prototype

```c
int aws_host_resolver_purge_cache(struct aws_host_resolver *resolver);
```
