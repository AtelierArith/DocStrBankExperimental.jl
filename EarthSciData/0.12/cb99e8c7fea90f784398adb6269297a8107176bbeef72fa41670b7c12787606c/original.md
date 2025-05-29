Create an `EarthSciMLBase.Operator` to write simulation output to a NetCDF file.

  * `filepath::String`: The path of the NetCDF file to write to
  * `file::Any`: The netcdf dataset
  * `vars::Any`: The netcdf variables corresponding to the state variables
  * `tvar::Any`: The netcdf variable for time
  * `h::Int64`: Current time index for writing
  * `time_interval::AbstractFloat`: Simulation time interval (in seconds) at which to write to disk
  * `extra_vars::AbstractVector`: Extra observed variables to write to disk
  * `extra_var_fs::AbstractVector`: Functions to get the extra vars
  * `grid::Any`: Spatial grid specification
  * `dtype::Any`: Data type of the output
