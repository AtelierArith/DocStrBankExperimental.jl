```
StochasticProgram(::Type{Scenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor=nothing) where Scenario <: AbstractScenario
```

Create a new two-stage stochastic program with scenarios of type `Scenario` and no stage data. Optionally, a capable `optimizer_constructor` can be supplied to later optimize the stochastic program.
