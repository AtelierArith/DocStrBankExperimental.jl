```
train!(ensemble::Bagging; kwargs...)
```

Trains all the model in an ensemble model - the keyword arguments are passed to `train!` for each model. Note that this retrains the *entire* model, which includes the transformers.
