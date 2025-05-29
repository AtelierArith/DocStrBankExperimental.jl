```
infer
```

Infer output type from input. Infer `AbstractDiagnostics` from corresponding `AbstractAlgorithm`

# Examples

```julia
infer(_rng, diagnostics::Type{AbstractDiagnostics}, algorithm, model, data)
```
