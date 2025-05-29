```
aws_memory_pool_release(mempool, to_release)
```

Releases memory to the pool if space is available, otherwise frees `to_release`

### Prototype

```c
void aws_memory_pool_release(struct aws_memory_pool *mempool, void *to_release);
```
