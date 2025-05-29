```
p8est_ghost_exchange_data(p8est_, ghost, ghost_data)
```

Transfer data for local quadrants that are ghosts to other processors. Send the data stored in the quadrant's user_data. This is either the pointer variable itself if `p8est`->data*size is 0, or the content of the referenced memory field if `p8est`->data\*size is positive.

### Parameters

  * `p8est`:[in] The forest used for reference.
  * `ghost`:[in] The ghost layer used for reference.
  * `ghost_data`:[in,out] Pre-allocated contiguous data for all ghost quadrants in sequence. If `p8est`->data_size is 0, must at least hold sizeof (void *) bytes for each, otherwise `p8est`->data_size each.

### Prototype

```c
void p8est_ghost_exchange_data (p8est_t * p8est, p8est_ghost_t * ghost, void *ghost_data);
```
