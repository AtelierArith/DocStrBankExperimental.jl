```
StochasticProgram(scenarios::Vector{<:AbstractScenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor = nothing)
```

Create a new two-stage stochastic program with a given collection of `scenarios` and no stage data. Optionally, a capable `optimizer_constructor` can be supplied to later optimize the stochastic program. If multiple Julia processes are available, the resulting stochastic program will automatically be memory-distributed on these processes. This can be avoided by setting `procs = [1]`.
