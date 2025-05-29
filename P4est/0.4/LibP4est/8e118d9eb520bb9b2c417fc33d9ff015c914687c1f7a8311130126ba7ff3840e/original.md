```
p8est_coarsen(p8est_, coarsen_recursive, coarsen_fn, init_fn)
```

Coarsen a forest.

### Parameters

  * `p8est`:[in,out] The forest is changed in place.
  * `coarsen_recursive`:[in] Boolean to decide on recursive coarsening.
  * `coarsen_fn`:[in] Callback function that returns true if a family of quadrants shall be coarsened
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.

### Prototype

```c
void p8est_coarsen (p8est_t * p8est, int coarsen_recursive, p8est_coarsen_t coarsen_fn, p8est_init_t init_fn);
```
