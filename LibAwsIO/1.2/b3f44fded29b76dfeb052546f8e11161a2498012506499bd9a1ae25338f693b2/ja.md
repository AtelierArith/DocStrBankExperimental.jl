```
aws_host_resolver_purge_cache(resolver)
```

!!! compat "非推奨"
    vtableのpurge*cacheを呼び出す代わりにpurge*cache*with*callbackを使用してください。


### プロトタイプ

```c
int aws_host_resolver_purge_cache(struct aws_host_resolver *resolver);
```
