```
aws_host_resolver_release(resolver)
```

ホストリゾルバの参照カウントを減少させます。参照カウントがゼロになると、リゾルバは破棄されます。

### プロトタイプ

```c
void aws_host_resolver_release(struct aws_host_resolver *resolver);
```
