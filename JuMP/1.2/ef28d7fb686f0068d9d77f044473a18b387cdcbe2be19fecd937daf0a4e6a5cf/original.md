```
relative_gap(model::Model)
```

Return the final relative optimality gap after a call to `optimize!(model)`. Exact value depends upon implementation of MathOptInterface.RelativeGap() by the particular solver used for optimization.
