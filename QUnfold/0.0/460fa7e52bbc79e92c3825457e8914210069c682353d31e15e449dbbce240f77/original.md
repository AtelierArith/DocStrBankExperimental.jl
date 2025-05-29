```
ClassTransformer(classifier; kwargs...)
```

This transformer yields the classification-based feature transformation used in `ACC`, `PACC`, `CC`, `PCC`, and `SLD`.

**Keyword arguments**

  * `is_probabilistic = false` whether or not to use posterior predictions.
  * `fit_classifier = true` whether or not to fit the given `classifier`.
