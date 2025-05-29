```
p8est_ghost_expand(p8est_, ghost)
```

Expand the size of the ghost layer and mirrors by one additional layer of adjacency.

### Parameters

  * `p8est`:[in] The forest from which the ghost layer was generated.
  * `ghost`:[in,out] The ghost layer to be expanded.

### Prototype

```c
void p8est_ghost_expand (p8est_t * p8est, p8est_ghost_t * ghost);
```
