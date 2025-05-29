```
sc_mempool_destroy(mempool)
```

Destroy a mempool structure. All elements that are still in use are invalidated.

### Parameters

  * `mempool`:[in,out] Its memory is freed.

### Prototype

```c
void sc_mempool_destroy (sc_mempool_t * mempool);
```
