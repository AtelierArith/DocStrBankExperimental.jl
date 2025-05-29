```
instantiate(stochasticmodel::StochasticModel{2};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            scenario_type::Type{S} = Scenario,
            defer::Bool = false,
            kw...) where S <: AbstractScenario
```

Instantiate a deferred two-stage stochastic program using the model definition stored in the two-stage `stochasticmodel` over the scenario type `S`. Optionally, supply an `optimizer`. If no explicit `instantiation` is provided, the structure is induced by the optimizer. The structure is `Deterministic` by default.
