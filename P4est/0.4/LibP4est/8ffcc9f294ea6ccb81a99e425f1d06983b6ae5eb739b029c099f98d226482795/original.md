```
p8est_load(filename, mpicomm, data_size, load_data, user_pointer, connectivity)
```

### Prototype

```c
p8est_t *p8est_load (const char *filename, sc_MPI_Comm mpicomm, size_t data_size, int load_data, void *user_pointer, p8est_connectivity_t ** connectivity);
```
