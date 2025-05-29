```
p4est_load_ext(filename, mpicomm, data_size, load_data, autopartition, broadcasthead, user_pointer, connectivity)
```

### Prototype

```c
p4est_t *p4est_load_ext (const char *filename, sc_MPI_Comm mpicomm, size_t data_size, int load_data, int autopartition, int broadcasthead, void *user_pointer, p4est_connectivity_t ** connectivity);
```
