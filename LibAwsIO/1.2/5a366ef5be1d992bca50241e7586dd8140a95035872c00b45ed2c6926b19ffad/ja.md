```
aws_host_resolver_purge_cache_with_callback(resolver, on_purge_cache_complete_callback, user_data)
```

[`aws_host_resolver_purge_cache_with_callback`](@ref) を vtable で呼び出すと、ホストリゾルバがキャッシュしているすべての情報が消去されます。

### プロトタイプ

```c
int aws_host_resolver_purge_cache_with_callback( struct aws_host_resolver *resolver, aws_simple_completion_callback *on_purge_cache_complete_callback, void *user_data);
```
