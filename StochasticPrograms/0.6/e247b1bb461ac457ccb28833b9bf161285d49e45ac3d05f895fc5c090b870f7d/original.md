```
instantiate(stochasticmodel::StochasticModel,
            scenarios::Vector{<:AbstractScenario};
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            defer::Bool = false,
            kw...)
```

Instantiate a stochastic program using the model definition stored in `stochasticmodel`, and the given collection of `scenarios`. Optionally, supply an `optimizer`. If no explicit `instantiation` is provided, the structure is induced by the optimizer. The structure is `Deterministic` by default.
