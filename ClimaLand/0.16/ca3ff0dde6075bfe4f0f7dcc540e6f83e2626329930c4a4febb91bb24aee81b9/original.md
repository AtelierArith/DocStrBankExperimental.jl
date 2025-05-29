```
 prescribed_lai_era5(era5_lai_ncdata_path,
                     era5_lai_cover_ncdata_path,
                     surface_space,
                     start_date,
                     earth_param_set;
                     time_interpolation_method = LinearInterpolation(PeriodicCalendar()),
                     regridder_type = :InterpolationsRegridder)
```

A helper function which constructs the TimeVaryingInput object for Leaf Area Index, from a file path pointing to the ERA5 LAI data in a netcdf file, a file path pointing to the ERA5 LAI cover data in a netcdf file, the surface*space, the start date, and the earth*param_set.

This currently one works when a single file is passed for both the era5 lai and era5 lai cover data.
