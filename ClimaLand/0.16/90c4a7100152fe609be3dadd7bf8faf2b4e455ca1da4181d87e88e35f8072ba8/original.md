```
 prescribed_forcing_era5(era5_ncdata_path,
                         surface_space,
                         start_date,
                         earth_param_set,
                         FT;
                         gustiness=1,
                         c_co2 = TimeVaryingInput((t) -> 4.2e-4),
                         time_interpolation_method = LinearInterpolation(PeriodicCalendar()),
                         regridder_type = :InterpolationsRegridder)
```

A helper function which constructs the `PrescribedAtmosphere` and `PrescribedRadiativeFluxes` from a file path pointing to the ERA5 data in a netcdf file, the surface*space, the start date, and the earth*param_set.

The argument `era5_ncdata_path` is either a list of nc files, each with all of the variables required, but with different time intervals in the different files, or else it is a single file with all the variables.
