```
p6est_coarsen_columns_ext(p6est_, coarsen_recursive, callback_orphans, coarsen_fn, init_fn, replace_fn)
```

Horizontally coarsen a forest.

### Parameters

  * `p6est`:[in,out] The forest is changed in place.
  * `coarsen_recursive`:[in] Boolean to decide on recursive coarsening.
  * `callback_orphans`:[in] Boolean to enable calling coarsen_fn even on non-families. In this case, the second quadrant pointer in the argument list of the callback is NULL, subsequent pointers are undefined, and the return value is ignored. If coarsen_recursive is true, it is possible that a quadrant is called once or more as an orphan and eventually becomes part of a family.
  * `coarsen_fn`:[in] Callback function that returns true if a family of quadrants shall be coarsened.
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically.
  * `replace_fn`:[in] Callback function that allows the user to change incoming quadrants based on the quadrants they replace.

### Prototype

```c
void p6est_coarsen_columns_ext (p6est_t * p6est, int coarsen_recursive, int callback_orphans, p6est_coarsen_column_t coarsen_fn, p6est_init_t init_fn, p6est_replace_t replace_fn);
```
