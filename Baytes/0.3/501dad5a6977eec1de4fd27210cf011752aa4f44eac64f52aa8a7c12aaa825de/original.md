```julia
struct SampleInfo{A<:Baytes.PrintedParameter, U<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool}
```

Contains several useful information for constructing sampler.

# Fields

  * `printedparam::Baytes.PrintedParameter`: Parameter settings for printing.
  * `iterations::Int64`: Total number of sampling iterations.
  * `burnin::Int64`: Burnin iterations.
  * `thinning::Int64`: Number of consecutive samples taken for diagnostics output.
  * `Nalgorithms::Int64`: Number of algorithms used while sampling.
  * `Nchains::Int64`: Number of chains used while sampling.
  * `captured::BaytesCore.UpdateBool`: Boolean if sampler need to be updated after a proposal run. This is the case for, e.g. PMCMC., or for adaptive tempering.
  * `tempered::BaytesCore.UpdateBool`: Boolean if temperature is adapted for target function.
