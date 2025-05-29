```
DEAC_Std(correlation_function::AbstractVector,
     correlation_function_error::AbstractVector,
     β::Float64,
     input_grid::Vector{Float64},
     out_ωs::Vector{Float64},
     kernel_type::String,
     num_bins::Int64,
     runs_per_bin::Int64,
     output_file::String,
     checkpoint_file::String;

     find_fitness_floor::Bool=true
     population_size::Int64=8,
     base_seed::Integer=8675309,
     number_of_generations::Int64=1000000,
     keep_bin_data=true,
     autoresume_from_checkpoint=false,
     verbose::Bool=false,
     
     fitness = 1.0,
     crossover_probability::Float64 = 0.9,
     self_adapting_crossover_probability::Float64 = 0.1,
     differential_weight::Float64 = 0.9,
     self_adapting_differential_weight_probability::Float64 = 0.1,
     self_adapting_differential_weight::Float64 = 0.9,
     user_mutation! = nothing 
     )
```

Runs the DEAC algorithm on data passed in `correlation_function` using $\Chi^2$ fitting from the error passed in by `correlation_function_error`.

# Arguments

  * `correlation_function::AbstractVector`: Input data in τ/ωₙ space
  * `correlation_function_error::AbstractVector`: Error associated with input data
  * `β::Float64`: Inverse temperature
  * `input_grid::Vector{Float64}`: Evenly spaced values in τ from 0 to β, including end points or ωₙ
  * `out_ωs::Vector{Float64}`: Evenly spaced energies for AC output
  * `kernel_type::String`: See below for allowable kernels
  * `num_bins::Int64`: Bins to generate
  * `runs_per_bin::Int64`: Number of runs per bin for statistics
  * `output_file::String`: File to store output dictionary. jld2 format recommended
  * `checkpoint_file::String`: File to store checkpoint data. jld2 format recommended

# Optional Arguments

  * `find_fitness_floor::Bool = false`: Find a reasonable floor for fitness and append that value to target fitnesses.
  * `population_size::Int64 = 8`: DEAC population size. Must be ≥ 6
  * `base_seed::Int64 = 8675309`: Seed
  * `number_of_generations::Int64 = 100000`: Maximum number of mutation loops
  * `keep_bin_data::Bool = true`: Save binned data or not
  * `autoresume_from_checkpoint::Bool = false`: Resume from checkpoint if possible
  * `verbose::Bool = false`: Print stats per run
  * `fitness = 1.0`: single value or an array of values for χ² fitting

# Optional algorithm arguments

  * `crossover_probability::Float64 = 0.9`: Starting likelihood of crossover
  * `self_adapting_crossover_probability::Float64 = 0.1`: Chance of crossover probability changing
  * `differential_weight::Float64 = 0.9`: Weight for second and third mutable indices
  * `self_adapting_differential_weight_probability::Float64 = 0.1`: Likelihood of SAD changing
  * `self_adapting_differential_weight::Float64 = 0.9`: SAD
  * `user_mutation! = nothing`: User passed function to add additional mutation to each iteration. See below for more information

Each run will use its own seed. E.g. if you run 10 bins with 100 runs per bin, you will use seeds `base_seed:base_seed+999`.  You may increment your base seed by 1000, use another output file name, and generate more statistics later.

# Output

SmoQyDEAC will save a dictionary to the file name passed via the `output_file` argument. The same dictionary will be returned by the function.

# Checkpointing

SmoQyDEAC will periodically save a file named according to the parameter passed in`checkpoint_file`. JLD2 format is recommended, e.g. a file with the .jld2 extension. After completing every bin this file will be saved. After the last bin is finished the file will be deleted. When `autoresume_from_checkpoint=true` SmoQyDEAC will attempt to resume from the checkpoint.  If the arguments passed do not match those in the checkpoint the code will exit.
