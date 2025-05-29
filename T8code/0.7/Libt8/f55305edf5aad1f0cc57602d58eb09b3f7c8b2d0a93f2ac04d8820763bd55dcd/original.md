```
t8_forest_write_netcdf(forest, file_prefix, file_title, dim, num_extern_netcdf_vars, ext_variables, comm)
```

### Prototype

```c
void t8_forest_write_netcdf (t8_forest_t forest, const char *file_prefix, const char *file_title, int dim, int num_extern_netcdf_vars, t8_netcdf_variable_t *ext_variables[], sc_MPI_Comm comm);
```
