```
sc_mempool_destroy_null(pmempool)
```

Destroy a mempool structure. All elements that are still in use are invalidated.

### Parameters

  * `pmempool`:[in,out] Address of pointer to memory pool. Its memory is freed, pointer is NULLed.

### Prototype

```c
void sc_mempool_destroy_null (sc_mempool_t ** pmempool);
```
