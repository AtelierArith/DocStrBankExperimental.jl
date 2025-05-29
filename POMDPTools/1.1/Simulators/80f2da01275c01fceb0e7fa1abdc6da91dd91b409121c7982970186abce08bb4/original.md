```
Sim(m::MDP, p::Policy[, initialstate]; kwargs...)
Sim(m::POMDP, p::Policy[, updater[, initial_belief[, initialstate]]]; kwargs...)
```

Create a Sim object that contains everything needed to run and record a single simulation, including model, initial conditions, and metadata.

A vector of `Sim` objects can be executed with [`run`](@ref) or [`run_parallel`](@ref).

## Keyword Arguments

  * `rng::AbstractRNG=Random.default_rng()`
  * `max_steps::Int=typemax(Int)`
  * `simulator::Simulator=HistoryRecorder(rng=rng, max_steps=max_steps)`
  * `metadata::NamedTuple a named tuple (or dictionary) of metadata for the sim that will be recorded, e.g.`(solver_iterations=500,)`.
