```
training(
    arg::TrainingArg, 
    net::NetworkArg, 
    rng_seed::Int
)
```

Train and return a trained `mlp` model, a Dict of training `logs` with train loss, training data loss and validation data loss for each epoch, and the `inputs` and `labels` (training data) the mlp was trained on. This function allows for both cpu and gpu training.
