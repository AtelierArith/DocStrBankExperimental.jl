```
run_particle_filter(
    init_model,
    input_file_path,
    observation_file_path,
    filter_type=BootstrapFilter,
    summary_stat_type=MeanAndVarSummaryStat;
    rng=Random.TaskLocalRNG()
) -> Tuple{Matrix, Union{NamedTuple, Nothing}}
```

Run particle filter. `init_model` is the function which initialise the model, `input_file_path` is the path to the YAML file with the input parameters. `observation_file_path` is the path to the HDF5 file containing the observation sequence to perform filtering for. `filter_type` is the particle filter type to use.   See [`ParticleFilter`](@ref) for the possible values. `summary_stat_type` is a type  specifying the summary statistics of the particles to compute at each time step. See  [`AbstractSummaryStat`](@ref) for the possible values. `rng` is a random number generator to use to generate random variates while filtering - a seeded random  number generator may be specified to ensure reproducible results. If running with multiple threads a thread-safe generator such as `Random.TaskLocalRNG` (the default) must be used.

Returns a tuple containing the state particles representing an estimate of the filtering distribution at the final observation time (with each particle a column of the returned matrix) and a named tuple containing the estimated summary statistics of this final  filtering distribution. If running on multiple ranks using MPI, the returned states array will correspond only to the particles local to this rank and the summary statistics will be returned only on the master rank with all other ranks returning `nothing` for their second return value.
