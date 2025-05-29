```
p6est_coarsen_layers(p6est_, coarsen_recursive, coarsen_fn, init_fn)
```

Coarsen the layers of a sheet.

### Parameters

  * `p6est`:[in,out] The forest is changed in place.
  * `coarsen_recursive`:[in] Boolean to decide on recursive coarsening.
  * `coarsen_fn`:[in] Callback function that returns true if a family of layers shall be coarsened
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.

### Prototype

```c
void p6est_coarsen_layers (p6est_t * p6est, int coarsen_recursive, p6est_coarsen_layer_t coarsen_fn, p6est_init_t init_fn);
```
