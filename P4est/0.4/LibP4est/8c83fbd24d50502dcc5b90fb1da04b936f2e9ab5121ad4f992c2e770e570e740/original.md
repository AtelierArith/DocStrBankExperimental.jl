```
p8est_memory_used(p8est_)
```

Calculate local memory usage of a forest structure. Not collective. The memory used on the current rank is returned. The connectivity structure is not counted since it is not owned; use p8est_connectivity_memory_usage (`p8est`->connectivity).

### Parameters

  * `p8est`:[in] Valid forest structure.

### Returns

Memory used in bytes.

### Prototype

```c
size_t p8est_memory_used (p8est_t * p8est);
```
