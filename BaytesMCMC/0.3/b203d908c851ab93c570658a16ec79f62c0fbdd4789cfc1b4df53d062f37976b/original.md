```julia
struct PhaseTune{T<:Tuple}
```

Information about current SamplingPhase.

# Fields

  * `update::BaytesCore.Updater`: Boolean if current iteration needs update.
  * `iter::BaytesCore.Iterator`: Counts current iteration in phase.
  * `counter::BaytesCore.Iterator`: MCMC Phases ~ counter = current cyle in slices/name/iterations.
  * `slices::Vector{Int64}`: Vector of MCMC iterations at each phase.
  * `name::Tuple`: Name of Sampling phases.
  * `iterations::Vector{Int64}`: Counts total iterations.
  * `window::Vector{Int64}`: Counts cycles in adaption phases Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ(),     i.e., 1-5-1 means 1 window init, 5 adapt, 1 exploration.
  * `buffer::Vector{Int64}`: Counts iteration in each cycle for adaption phases Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ(),     i.e., 50-25-50 means 1 time 50, 5 times 25*i, i in 1:5, 1 time 50.
