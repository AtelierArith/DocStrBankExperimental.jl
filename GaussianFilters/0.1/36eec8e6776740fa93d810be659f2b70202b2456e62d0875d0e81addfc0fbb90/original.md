```
simulation(filter::AbstractFilter, b0::GaussianBelief,
            action_sequence::Vector{AbstractVector}})
```

Run a simulation to get positions and measurements. Samples starting point from GaussianBelief b0, the runs action_sequence with additive gaussian noise all specified by AbstractFilter filter to return a simulated state and measurement history.
