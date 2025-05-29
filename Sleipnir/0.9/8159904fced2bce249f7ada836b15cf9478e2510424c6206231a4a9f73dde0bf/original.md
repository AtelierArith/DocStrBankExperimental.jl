A structure to hold simulation parameters for a simulation in ODINN.

```
struct SimulationParameters{I <: Integer, F <: AbstractFloat, VM <: VelocityMapping} <: AbstractParameters
```

# Fields

  * `use_MB::Bool`: Flag to indicate whether mass balance should be used.
  * `use_iceflow::Bool`: Flag to indicate whether ice flow should be used.
  * `plots::Bool`: Flag to indicate whether plots should be generated.
  * `velocities::Bool`: Flag to indicate whether velocities should be calculated.
  * `overwrite_climate::Bool`: Flag to indicate whether to overwrite climate data.
  * `use_glathida_data::Bool`: Flag to indicate whether to use GLATHIDA data.
  * `tspan::Tuple{F, F}`: Time span for the simulation.
  * `step::F`: Time step for the simulation.
  * `multiprocessing::Bool`: Flag to indicate whether multiprocessing should be used.
  * `workers::I`: Number of workers for multiprocessing.
  * `working_dir::String`: Directory for working files.
  * `test_mode::Bool`: Flag to indicate whether to run in test mode.
  * `rgi_paths::Dict{String, String}`: Dictionary of RGI paths.
  * `ice_thickness_source::String`: Source of ice thickness data.
  * `mapping::VM`: Mapping to use in order to grid the data from the coordinates of   the velocity product datacube to the glacier grid.
  * `gridScalingFactor::I`: Grid downscaling factor, used to speed-up the tests.   Default value is 1 which means no downscaling is applied.
