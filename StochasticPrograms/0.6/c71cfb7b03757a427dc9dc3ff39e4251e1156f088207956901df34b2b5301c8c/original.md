```
supports_structure(optimizer::StochasticProgramOptimizerType, structure::AbstractStochasticStructure)
```

Return a `Bool` indicating whether `optimizer` supports the stochastic `structure`. That is, `load_structure!(optimizer, structure)` will not throw `UnsupportedStructure`
