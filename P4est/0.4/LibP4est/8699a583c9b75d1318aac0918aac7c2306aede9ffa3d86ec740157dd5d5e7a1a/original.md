```
p8est_ghost_exchange_custom(p8est_, ghost, data_size, mirror_data, ghost_data)
```

Transfer data for local quadrants that are ghosts to other processors. The data size is the same for all quadrants and can be chosen arbitrarily.

### Parameters

  * `p8est`:[in] The forest used for reference.
  * `ghost`:[in] The ghost layer used for reference.
  * `data_size`:[in] The data size to transfer per quadrant.
  * `mirror_data`:[in] One data pointer per mirror quadrant.
  * `ghost_data`:[in,out] Pre-allocated contiguous data for all ghosts in sequence, which must hold at least `data_size` for each ghost.

### Prototype

```c
void p8est_ghost_exchange_custom (p8est_t * p8est, p8est_ghost_t * ghost, size_t data_size, void **mirror_data, void *ghost_data);
```
