```
write_hparams!(logger::TBLogger, hparams::Dict{String, Any}, metrics::AbstractArray{String})
```

Writes the supplied hyperparameters to the logger, along with noting all metrics that should be tracked.

The value of `hparams` can be a `String`, `Bool` or a subtype of `Real`. All `Real` values are converted to `Float64` when writing the logs.

`metrics` should be a list of tags, which correspond to scalars that have been logged. Tensorboard will automatically extract the latest metric logged to use for this value.
