```
instantiate(stochasticmodel::StochasticModel,
            sampler::AbstractSampler,
            n::Integer;
            instantiation::StochasticInstantiation = UnspecifiedInstantiation(),
            optimizer = nothing,
            defer::Bool = false,
            kw...)
```

Generate a sampled instance of size `n` using the model stored in the two-stage `stochasticmodel`, and the provided `sampler`. Optionally, supply an `optimizer`. If no explicit `instantiation` is provided, the structure is induced by the optimizer. The structure is `Deterministic` by default.
