```
aws_host_resolver_acquire(resolver)
```

Increments the reference count on the host resolver, allowing the caller to take a reference to it.

Returns the same host resolver passed in.

### Prototype

```c
struct aws_host_resolver *aws_host_resolver_acquire(struct aws_host_resolver *resolver);
```
