```
p8est_ghost_is_valid(p8est_, ghost)
```

Examine if a ghost structure is valid as desribed above. Test if within a ghost-structure the arrays ghosts and mirrors are in p8est_quadrant_compare_piggy order. Test if local_num in piggy3 data member of the quadrants in ghosts and mirrors are in ascending order (ascending within each rank for ghost).

Test if the [`p4est_locidx_t`](@ref) arrays are in ascending order (for mirror_proc_mirrors ascending within each rank)

### Parameters

  * `p8est`:[in] the forest.
  * `ghost`:[in] Ghost layer structure.

### Returns

true if *ghost* is valid

### Prototype

```c
int p8est_ghost_is_valid (p8est_t * p8est, p8est_ghost_t * ghost);
```
