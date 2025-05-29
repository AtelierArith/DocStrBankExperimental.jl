```
train_loop!(
    mlp::Chain, 
    arg::TrainingArg, 
    inputs::Array{Float64,2}, 
    labels::Array{Float64,2}
)
```

Train and update the `mlp` and return a Dict of training logs with train loss, training data loss and validation data loss for each epoch. This function works on cpu, which is sufficiently fast for most cases.
