```
p4est_ghost_new(p4est_, btype)
```

Builds the ghost layer.

This will gather the quadrants from each neighboring proc to build one layer of face and corner based ghost elements around the ones they own.

### Parameters

  * `p4est`:[in] The forest for which the ghost layer will be generated.
  * `btype`:[in] Which ghosts to include (across face, corner or full).

### Returns

A fully initialized ghost layer.

### Prototype

```c
p4est_ghost_t *p4est_ghost_new (p4est_t * p4est, p4est_connect_type_t btype);
```
