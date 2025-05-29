```
aws_host_resolver_purge_cache_with_callback(resolver, on_purge_cache_complete_callback, user_data)
```

Calls [`aws_host_resolver_purge_cache_with_callback`](@ref) on the vtable which will wipe out everything host resolver has cached.

### Prototype

```c
int aws_host_resolver_purge_cache_with_callback( struct aws_host_resolver *resolver, aws_simple_completion_callback *on_purge_cache_complete_callback, void *user_data);
```
