```
p4est_ghost_exchange_custom(p4est_, ghost, data_size, mirror_data, ghost_data)
```

Transfer data for local quadrants that are ghosts to other processors. The data size is the same for all quadrants and can be chosen arbitrarily.

### Parameters

  * `p4est`:[in] The forest used for reference.
  * `ghost`:[in] The ghost layer used for reference.
  * `data_size`:[in] The data size to transfer per quadrant.
  * `mirror_data`:[in] One data pointer per mirror quadrant as input.
  * `ghost_data`:[in,out] Pre-allocated contiguous data for all ghosts in sequence, which must hold at least `data_size` for each ghost.

### Prototype

```c
void p4est_ghost_exchange_custom (p4est_t * p4est, p4est_ghost_t * ghost, size_t data_size, void **mirror_data, void *ghost_data);
```
