```
StochasticProgram(first_stage_params::Any,
                  second_stage_params::Any,
                  ::Type{Scenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor=nothing) where Scenario <: AbstractScenario
```

Create a new two-stage stochastic program with stage data given by `first_stage_params` and `second_stage_params`. After construction, scenarios of type `S` can be added through `add_scenario!`. Optionally, a capable `optimizer_constructor` can be supplied to later optimize the stochastic program. If multiple Julia processes are available, the resulting stochastic program will automatically be memory-distributed on these processes. This can be avoided by setting `procs = [1]`.
