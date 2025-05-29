```
p8est_new_ext(mpicomm, connectivity, min_quadrants, min_level, fill_uniform, data_size, init_fn, user_pointer)
```

### Prototype

```c
p8est_t *p8est_new_ext (sc_MPI_Comm mpicomm, p8est_connectivity_t * connectivity, p4est_locidx_t min_quadrants, int min_level, int fill_uniform, size_t data_size, p8est_init_t init_fn, void *user_pointer);
```
