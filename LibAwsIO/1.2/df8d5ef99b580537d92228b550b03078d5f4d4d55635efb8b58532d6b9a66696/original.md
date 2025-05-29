```
aws_client_bootstrap_acquire(bootstrap)
```

Increments a client bootstrap's ref count, allowing the caller to take a reference to it.

Returns the same client bootstrap passed in.

### Prototype

```c
struct aws_client_bootstrap *aws_client_bootstrap_acquire(struct aws_client_bootstrap *bootstrap);
```
