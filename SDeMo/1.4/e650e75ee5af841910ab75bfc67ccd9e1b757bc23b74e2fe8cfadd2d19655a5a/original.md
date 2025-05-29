```
train!(ensemble::Ensemble; kwargs...)
```

Trains all the model in an heterogeneous ensemble model - the keyword arguments are passed to `train!` for each model. Note that this retrains the *entire* model, which includes the transformers.

The keywod arguments are passed to `train!` and can include the `training` indices.
