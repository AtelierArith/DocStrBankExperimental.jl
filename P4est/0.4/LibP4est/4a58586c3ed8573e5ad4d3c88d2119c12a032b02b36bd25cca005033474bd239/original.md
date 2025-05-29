```
p8est_ghost_new(p8est_, btype)
```

Builds the ghost layer.

This will gather the quadrants from each neighboring proc to build one layer of face, edge and corner based ghost elements around the ones they own.

### Parameters

  * `p8est`:[in] The forest for which the ghost layer will be generated.
  * `btype`:[in] Which ghosts to include (across face, edge, or corner/full).

### Returns

A fully initialized ghost layer.

### Prototype

```c
p8est_ghost_t *p8est_ghost_new (p8est_t * p8est, p8est_connect_type_t btype);
```
