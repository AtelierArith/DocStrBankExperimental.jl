```
aws_host_resolver_release(resolver)
```

Decrements a host resolver's ref count. When the ref count drops to zero, the resolver will be destroyed.

### Prototype

```c
void aws_host_resolver_release(struct aws_host_resolver *resolver);
```
