```julia
struct SampleDefault{D<:BaytesCore.DataStructure, M<:BaytesCore.TemperingMethod, P<:BaytesCore.ProgressReport}
```

Default arguments for sampling routine.

# Fields

  * `dataformat::BaytesCore.DataStructure`: Format to split data before proposal step.
  * `tempering::BaytesCore.TemperingMethod`: Tempering values for target distributions of each chain, per default = 1*logtarget(θ | data) for each chain
  * `chains::Int64`: Number of chains run in sampling step.
  * `iterations::Int64`: Number of MCMC iterations. May be overwritten in SMC.
  * `burnin::Int64`: Burn in samples.
  * `thinning::Int64`: Number of consecutive samples taken for diagnostics output.
  * `safeoutput::Bool`: Boolean if trace and algorithm should be safed to working directory.
  * `printoutput::Bool`: Boolean if summary statistics should be calculated.
  * `printdefault::BaytesCore.PrintDefault`: Default arguments for printing summary statistics
  * `report::BaytesCore.ProgressReport`: Default arguments for printing output during sampling runs
