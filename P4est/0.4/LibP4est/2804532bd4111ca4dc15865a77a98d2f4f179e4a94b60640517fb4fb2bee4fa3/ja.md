```
p6est_new_ext(mpicomm, connectivity, min_quadrants, min_level, min_zlevel, num_zroot, fill_uniform, data_size, init_fn, user_pointer)
```

### プロトタイプ

```c
p6est_t *p6est_new_ext (sc_MPI_Comm mpicomm, p6est_connectivity_t * connectivity, p4est_locidx_t min_quadrants, int min_level, int min_zlevel, int num_zroot, int fill_uniform, size_t data_size, p6est_init_t init_fn, void *user_pointer);
```
