```
WarmUp
```

The Warm Up method prepares a warmup system with the Total Degree method using the parameter at `index` perturbed by `perturbation_size`. The warmup system is used to perform a homotopy using all other systems in the parameter sweep. It is very efficient for systems with minimal bifurcation in the parameter sweep. The Warm Up method should in theory guarantee to find all solutions, however, if the `start_parameters` is not proper (to close to the real line) it could miss some solutions.

See[HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/many-systems/) for more information.

# Fields

  * `warm_up_method::Union{HarmonicSteadyState.Polyhedral{T}, HarmonicSteadyState.TotalDegree{T}} where T`: Method used for the warmup system.
  * `start_parameters::Vector`: Start parameters.
  * `thread::Bool`: Boolean indicating if threading is enabled.
  * `check_zero::Bool`: Check if zero is a root
  * `tracker_options::HomotopyContinuation.TrackerOptions`: Options for the tracker.
  * `endgame_options::HomotopyContinuation.EndgameOptions`: Options for the endgame.
  * `compile::Union{Bool, Symbol}`: Compilation options.
  * `seed::UInt32`: Seed for random number generation.
