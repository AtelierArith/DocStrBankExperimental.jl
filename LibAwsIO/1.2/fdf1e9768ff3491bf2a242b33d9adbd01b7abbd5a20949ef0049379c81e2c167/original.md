```
aws_server_bootstrap_acquire(bootstrap)
```

Increments a server bootstrap's ref count, allowing the caller to take a reference to it.

Returns the same server bootstrap passed in.

### Prototype

```c
struct aws_server_bootstrap *aws_server_bootstrap_acquire(struct aws_server_bootstrap *bootstrap);
```
