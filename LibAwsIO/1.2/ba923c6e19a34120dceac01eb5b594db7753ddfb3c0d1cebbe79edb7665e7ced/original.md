```
aws_server_bootstrap_release(bootstrap)
```

Decrements a server bootstrap's ref count. When the ref count drops to zero, the bootstrap will be destroyed.

### Prototype

```c
void aws_server_bootstrap_release(struct aws_server_bootstrap *bootstrap);
```
