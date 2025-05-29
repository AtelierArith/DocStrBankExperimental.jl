```
p8est_reset_data(p8est_, data_size, init_fn, user_pointer)
```

Reset user pointer and element data. When the data size is changed the quadrant data is freed and allocated. The initialization callback is invoked on each quadrant. Old user_data content is disregarded.

### Parameters

  * `data_size`:[in] This is the size of data for each quadrant which can be zero. Then user_data_pool is set to NULL.
  * `init_fn`:[in] Callback function to initialize the user_data which is already allocated automatically. May be NULL.
  * `user_pointer`:[in] Assign to the user_pointer member of the `p8est` before init_fn is called the first time.

### Prototype

```c
void p8est_reset_data (p8est_t * p8est, size_t data_size, p8est_init_t init_fn, void *user_pointer);
```
