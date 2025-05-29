A ParticleTracker is implemented as a callback to output the trajectories of particles from particle advection. To be added like

```
add!(model.callbacks, ParticleTracker(spectral_grid; kwargs...))
```

Output done via netCDF. Fields and options are

  * `schedule::SpeedyWeather.Schedule`: [OPTION] when to schedule particle tracking
  * `file_name::String`: [OPTION] File name for netCDF file
  * `compression_level::Int64`: [OPTION] lossless compression level; 1=low but fast, 9=high but slow
  * `shuffle::Bool`: [OPTION] shuffle/bittranspose filter for compression
  * `keepbits::Int64`: [OPTION] mantissa bits to keep, (14, 15, 16) means at least (2km, 1km, 500m) accurate locations
  * `nparticles::Int64`: Number of particles to track
  * `netcdf_file::Union{Nothing, NCDatasets.NCDataset}`: The netcdf file to be written into, will be created at initialization
  * `lon::Vector`
  * `lat::Vector`
  * `σ::Vector`
