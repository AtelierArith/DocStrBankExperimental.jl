```
t8_netcdf_create_var(var_type, var_name, var_long_name, var_unit, var_data)
```

Create an extern double variable which additionally should be put out to the NetCDF File

# Arguments

  * `var_type`:[in] Defines the datatype of the variable, either T8_NETCDF_INT, T8_NETCDF_INT64 or T8_NETCDF_DOUBLE.
  * `var_name`:[in] A String which will be the name of the created variable.
  * `var_long_name`:[in] A string describing the variable a bit more and what it is about.
  * `var_unit`:[in] The units in which the data is provided.
  * `var_data`:[in] A [`sc_array_t`](@ref) holding the elementwise data of the variable.
  * `num_extern_netcdf_vars`:[in] The number of extern user-defined variables which hold elementwise data (if none, set it to 0).

### Prototype

```c
t8_netcdf_variable_t * t8_netcdf_create_var (t8_netcdf_variable_type_t var_type, const char *var_name, const char *var_long_name, const char *var_unit, sc_array_t *var_data);
```
