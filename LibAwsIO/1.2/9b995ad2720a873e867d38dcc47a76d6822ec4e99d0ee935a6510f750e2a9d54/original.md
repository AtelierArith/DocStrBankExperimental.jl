```
aws_memory_pool_acquire(mempool)
```

Acquires memory from the pool if available, otherwise, it attempts to allocate and returns the result.

### Prototype

```c
void *aws_memory_pool_acquire(struct aws_memory_pool *mempool);
```
