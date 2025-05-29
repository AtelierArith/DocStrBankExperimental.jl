```
instantiate(stochasticmodel::StochasticModel{2},
            scenarios::Vector{<:AbstractScenario};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing;
            defer::Bool = false,
            kw...)
```

Instantiate a two-stage stochastic program using the model definition stored in the two-stage `stochasticmodel`, and the given collection of `scenarios`. Optionally, supply an `optimizer`. If no explicit `instantiation` is provided, the structure is induced by the optimizer. The structure is `Deterministic` by default.
