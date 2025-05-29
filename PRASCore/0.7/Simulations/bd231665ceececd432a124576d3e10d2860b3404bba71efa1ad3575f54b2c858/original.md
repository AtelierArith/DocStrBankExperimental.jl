```
assess(system::SystemModel, method::SequentialMonteCarlo, resultspecs::ResultSpec...)
```

Run a Sequential Monte Carlo simulation on a `system` using the `method` data and return `resultspecs`.

# Arguments

  * `system::SystemModel`: PRAS data structure
  * `method::SequentialMonteCarlo`: method for PRAS analysis
  * `resultspecs::ResultSpec...`: PRAS metric for metrics like [`Shortfall`](@ref) missing generation

# Returns

  * `results::Tuple{Vararg{ResultAccumulator{SequentialMonteCarlo}}}`: PRAS metric results
