```
aws_client_bootstrap_release(bootstrap)
```

Decrements a client bootstrap's ref count. When the ref count drops to zero, the bootstrap will be destroyed.

### Prototype

```c
void aws_client_bootstrap_release(struct aws_client_bootstrap *bootstrap);
```
