```
p8est_ghost_exchange_custom_levels(p8est_, ghost, minlevel, maxlevel, data_size, mirror_data, ghost_data)
```

Transfer data for local quadrants that are ghosts to other processors. The data size is the same for all quadrants and can be chosen arbitrarily. This function restricts the transfer to a range of refinement levels. The memory for quadrants outside the level range is not dereferenced.

### Parameters

  * `p8est`:[in] The forest used for reference.
  * `ghost`:[in] The ghost layer used for reference.
  * `minlevel`:[in] Level of the largest quads to be exchanged. Use <= 0 for no restriction.
  * `maxlevel`:[in] Level of the smallest quads to be exchanged. Use >= `P8EST_QMAXLEVEL` for no restriction.
  * `data_size`:[in] The data size to transfer per quadrant.
  * `mirror_data`:[in] One data pointer per mirror quadrant as input.
  * `ghost_data`:[in,out] Pre-allocated contiguous data for all ghosts in sequence, which must hold at least `data_size` for each ghost.

### Prototype

```c
void p8est_ghost_exchange_custom_levels (p8est_t * p8est, p8est_ghost_t * ghost, int minlevel, int maxlevel, size_t data_size, void **mirror_data, void *ghost_data);
```
