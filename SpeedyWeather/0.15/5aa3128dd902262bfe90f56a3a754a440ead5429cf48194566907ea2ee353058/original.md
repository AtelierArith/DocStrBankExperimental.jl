Output writer for a netCDF file with (re-)gridded variables. Interpolates non-rectangular grids. Fields are

  * `active::Bool`
  * `path::String`: [OPTION] path to output folder, run_???? will be created within
  * `id::String`: [OPTION] run identification number/string
  * `run_path::String`
  * `filename::String`: [OPTION] name of the output netcdf file
  * `write_restart::Bool`: [OPTION] also write restart file if output==true?
  * `pkg_version::VersionNumber`
  * `startdate::Dates.DateTime`
  * `output_dt::Dates.Second`: [OPTION] output frequency, time step
  * `variables::Dict{Symbol, SpeedyWeather.AbstractOutputVariable}`: [OPTION] dictionary of variables to output, e.g. u, v, vor, div, pres, temp, humid
  * `output_every_n_steps::Int64`
  * `timestep_counter::Int64`
  * `output_counter::Int64`
  * `netcdf_file::Union{Nothing, NCDatasets.NCDataset}`
  * `interpolator::Any`
  * `grid2D::Any`
  * `grid3D::Any`
  * `grid3Dland::Any`
