```
default_structure(instantiation::StochasticInstantiation, optimizer)
```

Returns a `StochasticInstantiation` based on the provided `instantiation` and `optimizer`. If an explicit `instantiation` is provided it is always prioritized. Otherwise, if `instantiation` is `UnspecifiedInstantiation`, returns whatever structure requested by the optimizer. Defaults to `Deterministic` if no optimizer is provided.
