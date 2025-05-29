```
t8_forest_write_netcdf_ext(forest, file_prefix, file_title, dim, num_extern_netcdf_vars, ext_variables, comm, netcdf_var_storage_mode, netcdf_var_mpi_access)
```

### Prototype

```c
void t8_forest_write_netcdf_ext (t8_forest_t forest, const char *file_prefix, const char *file_title, int dim, int num_extern_netcdf_vars, t8_netcdf_variable_t *ext_variables[], sc_MPI_Comm comm, int netcdf_var_storage_mode, int netcdf_var_mpi_access);
```
