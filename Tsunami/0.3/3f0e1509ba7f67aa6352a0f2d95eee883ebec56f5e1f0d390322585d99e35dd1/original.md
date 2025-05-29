```
FitState
```

A type storing the state of execution during a call to [`fit!`](@ref). 

A `FitState` object is part of a [`Trainer`](@ref) object.

# Fields

  * `epoch`: the current epoch number.
  * `run_dir`: the directory where the logs and checkpoints are saved.
  * `stage`: the current stage of execution. One of `:training`, `:train_epoch_end`, `:validation`, `:val_epoch_end`.
  * `step`: the current step number.
  * `batchsize`: number of samples in the current batch.
  * `should_stop`: set to `true` to stop the training loop.
