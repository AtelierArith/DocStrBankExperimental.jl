```
p4est_ghost_expand(p4est_, ghost)
```

Expand the size of the ghost layer and mirrors by one additional layer of adjacency.

### Parameters

  * `p4est`:[in] The forest from which the ghost layer was generated.
  * `ghost`:[in,out] The ghost layer to be expanded.

### Prototype

```c
void p4est_ghost_expand (p4est_t * p4est, p4est_ghost_t * ghost);
```
