```julia
struct TransformInfo
```

Contains arguments for trace to extract parameter. Used to construct a 'TraceTransform'.

# Fields

  * `chains::Vector{Int64}`: Chain indices that are used for output diagnostics.
  * `algorithms::Vector{Int64}`: Algorithm indices that are used for output diagnostics.
  * `burnin::Int64`: Number of burnin steps before output diagnostics are taken.
  * `thinning::Int64`: Number of steps that are set between 2 consecutive samples.
  * `maxiterations::Int64`: Maximum number of iterations to be collected for each chain.
  * `effective_iterations::StepRange{Int64, Int64}`: StepRange for indices of effective samples
