```
p4est_ghost_bsearch(ghost, which_proc, which_tree, q)
```

Conduct binary search for exact match on a range of the ghost layer.

### Parameters

  * `ghost`:[in] The ghost layer.
  * `which_proc`:[in] The owner of the searched quadrant. Can be -1.
  * `which_tree`:[in] The tree of the searched quadrant. Can be -1.
  * `q`:[in] Valid quadrant is searched in the ghost layer.

### Returns

Offset in the ghost layer, or -1 if not found.

### Prototype

```c
ssize_t p4est_ghost_bsearch (p4est_ghost_t * ghost, int which_proc, p4est_topidx_t which_tree, const p4est_quadrant_t * q);
```
