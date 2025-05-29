```
p4est_ghost_checksum(p4est_, ghost)
```

Compute the parallel checksum of a ghost layer.

### Parameters

  * `p4est`:[in] The MPI information of this `p4est` will be used.
  * `ghost`:[in] A ghost layer obtained from the `p4est`.

### Returns

Parallel checksum on rank 0, 0 otherwise.

### Prototype

```c
unsigned p4est_ghost_checksum (p4est_t * p4est, p4est_ghost_t * ghost);
```
