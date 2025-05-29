```
p8est_load_ext(filename, mpicomm, data_size, load_data, autopartition, broadcasthead, user_pointer, connectivity)
```

### Prototype

```c
p8est_t *p8est_load_ext (const char *filename, sc_MPI_Comm mpicomm, size_t data_size, int load_data, int autopartition, int broadcasthead, void *user_pointer, p8est_connectivity_t ** connectivity);
```
