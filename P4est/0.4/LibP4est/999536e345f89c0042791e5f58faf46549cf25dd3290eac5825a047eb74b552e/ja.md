```
p4est_source_ext(src, mpicomm, data_size, load_data, autopartition, broadcasthead, user_pointer, connectivity)
```

### プロトタイプ

```c
p4est_t *p4est_source_ext (sc_io_source_t * src, sc_MPI_Comm mpicomm, size_t data_size, int load_data, int autopartition, int broadcasthead, void *user_pointer, p4est_connectivity_t ** connectivity);
```
