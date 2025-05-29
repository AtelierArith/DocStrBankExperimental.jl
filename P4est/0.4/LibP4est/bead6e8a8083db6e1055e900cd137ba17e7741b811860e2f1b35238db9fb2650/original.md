```
p6est_new_from_p4est(p4est_, top_vertices, height, min_zlevel, data_size, init_fn, user_pointer)
```

Create a new forest from an already created `p4est` that represents columns.

### Parameters

  * `p4est`:[in] A valid `p4est`. A deep copy will be created, so this can be destroyed without affectin the new `p6est` object.
  * `top_vertices`:[in] the same as in p6est_conectivity_new()
  * `height`:[in] the same as in p6est_conectivity_new()
  * `min_zlevel`:[in] the same as in [`p6est_new`](@ref)()
  * `data_size`:[in] the same as in [`p6est_new`](@ref)()
  * `init_fn`:[in] the same as in [`p6est_new`](@ref)()
  * `user_pointer`:[in] the same as in [`p6est_new`](@ref)()

### Returns

This returns a valid forest. The user must destroy the connectivity for the new `p6est` independently.

### Prototype

```c
p6est_t *p6est_new_from_p4est (p4est_t * p4est, double *top_vertices, double height[3], int min_zlevel, size_t data_size, p6est_init_t init_fn, void *user_pointer);
```
