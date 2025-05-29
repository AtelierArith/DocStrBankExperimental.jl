```
p8est_ghost_checksum(p8est_, ghost)
```

Compute the parallel checksum of a ghost layer.

### Parameters

  * `p8est`:[in] The MPI information of this `p8est` will be used.
  * `ghost`:[in] A ghost layer obtained from the `p8est`.

### Returns

Parallel checksum on rank 0, 0 otherwise.

### Prototype

```c
unsigned p8est_ghost_checksum (p8est_t * p8est, p8est_ghost_t * ghost);
```
