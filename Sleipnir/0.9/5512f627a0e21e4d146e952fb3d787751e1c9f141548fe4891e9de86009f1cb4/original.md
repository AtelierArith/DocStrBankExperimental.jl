Constructor for `SimulationParameters` type, including default values.

```
SimulationParameters(;
    use_MB::Bool = true,
    use_iceflow::Bool = true,
    plots::Bool = true,
    velocities::Bool = true,
    overwrite_climate::Bool = false,
    use_glathida_data::Bool = false,
    tspan::Tuple{F, F} = (2010.0,2015.0),
    step::F = 1/12,
    multiprocessing::Bool = true,
    workers::I = 4,
    working_dir::String = "",
    test_mode::Bool = false,
    rgi_paths::Dict{String, String} = Dict{String, String}(),
    ice_thickness_source::String = "Farinotti19",
    mapping::VM = MeanDateVelocityMapping(),
    gridScalingFactor::I = 1,
) where {I <: Integer, F <: AbstractFloat, VM <: VelocityMapping}
```

# Keyword arguments

  * `use_MB::Bool`: Whether to use mass balance (default: `true`).
  * `use_iceflow::Bool`: Whether to use ice flow (default: `true`).
  * `plots::Bool`: Whether to generate plots (default: `true`).
  * `velocities::Bool`: Whether to calculate velocities (default: `true`).
  * `overwrite_climate::Bool`: Whether to overwrite climate data (default: `false`).
  * `use_glathida_data::Bool`: Whether to use GLATHIDA data (default: `false`).
  * `float_type::DataType`: Data type for floating point numbers (default: `Float64`).
  * `int_type::DataType`: Data type for integers (default: `Int64`).
  * `tspan::Tuple{F, F}`: Time span for the simulation (default: `(2010.0, 2015.0)`).
  * `step::F`: Time step for the simulation (default: `1/12`).
  * `multiprocessing::Bool`: Whether to use multiprocessing (default: `true`).
  * `workers::I`: Number of workers for multiprocessing (default: `4`).
  * `working_dir::String`: Working directory for the simulation (default: `""`).
  * `test_mode::Bool`: Whether to run in test mode (default: `false`).
  * `rgi_paths::Dict{String, String}`: Dictionary of RGI paths (default: `Dict{String, String}()`).
  * `ice_thickness_source::String`: Source of ice thickness data, either `"Millan22"` or `"Farinotti19"` (default: `"Farinotti19"`).
  * `mapping::VM`: Mapping to use in order to grid the data from the coordinates of   the velocity product datacube to the glacier grid.
  * `gridScalingFactor::I`: Grid downscaling factor, used to speed-up the tests.   Default value is 1 which means no downscaling is applied.

# Returns

  * `simulation_parameters`: A new `SimulationParameters` object.

# Throws

  * `AssertionError`: If `ice_thickness_source` is not `"Millan22"` or `"Farinotti19"`.

# Notes

  * If the global variable ODINN*OVERWRITE*MULTI is set to true, multiprocessing is   disabled in any case. This is to fix the documentation generation as for the   moment Literate.jl freezes when multiprocessing is enabled.
