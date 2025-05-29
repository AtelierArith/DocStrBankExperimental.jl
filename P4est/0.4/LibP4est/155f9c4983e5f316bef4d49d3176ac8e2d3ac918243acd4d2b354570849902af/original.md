```
p4est_memory_used(p4est_)
```

Calculate local memory usage of a forest structure. Not collective. The memory used on the current rank is returned. The connectivity structure is not counted since it is not owned; use p4est_connectivity_memory_usage (`p4est`->connectivity).

### Parameters

  * `p4est`:[in] Valid forest structure.

### Returns

Memory used in bytes.

### Prototype

```c
size_t p4est_memory_used (p4est_t * p4est);
```
