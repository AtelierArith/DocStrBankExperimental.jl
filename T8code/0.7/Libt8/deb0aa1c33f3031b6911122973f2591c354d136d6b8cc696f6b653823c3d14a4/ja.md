```
t8_cmesh_write_netcdf(cmesh, file_prefix, file_title, dim, num_extern_netcdf_vars, variables, comm)
```

### プロトタイプ

```c
void t8_cmesh_write_netcdf (t8_cmesh_t cmesh, const char *file_prefix, const char *file_title, int dim, int num_extern_netcdf_vars, t8_netcdf_variable_t *variables[], sc_MPI_Comm comm);
```
