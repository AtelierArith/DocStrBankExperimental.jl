```
smooth_vars_and_write_to_netcdf!(output_file,input_file,vars_to_smooth,window_h,window_t)
```

Take a netcdf file, a list of variables and two integers and performs a moving mean smoothing of these variables. Write the smoothed fields into a netcdf file called output_file
