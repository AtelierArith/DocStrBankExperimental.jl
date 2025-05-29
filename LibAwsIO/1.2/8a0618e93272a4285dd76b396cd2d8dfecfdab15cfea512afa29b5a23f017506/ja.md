```
aws_host_resolver_purge_host_cache(resolver, options)
```

ホストのキャッシュを非同期で削除します。

### プロトタイプ

```c
int aws_host_resolver_purge_host_cache( struct aws_host_resolver *resolver, const struct aws_host_resolver_purge_host_options *options);
```
