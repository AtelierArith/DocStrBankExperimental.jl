```
nestedmodels(modeltype::Type{FixedEffectModel}, f::FormulaTerm, data; null = true, kwargs...)
```

Generate nested models from modeltype, formula and data. The null model will be an empty model if the keyword argument null is true (default).
