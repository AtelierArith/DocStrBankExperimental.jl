```
readmetrics(m::AbstractModel; round_digits = nothing)
```

Return a `NamedTuple` with some performance metrics for the given symbolic model. Performance metrics can be computed when the `info` structure of the model has the following keys:

  * `:supporting_labels`
  * `:supporting_predictions`

The `round_digits` keyword argument, if provided, is used to `round` accuracy/confidence metrics.
