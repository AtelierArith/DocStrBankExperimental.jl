```julia
sci_train!(ann, data; ...)
sci_train!(ann, data, opt; device, epoch, batch)

```

Scientific machine learning trainer

# Arguments

  * $ann$: neural network model
  * $data$: tuple (X, Y) of dataset
  * $opt$: optimizer
  * $epoch$: epoch number
  * $batch$: batch size
  * $device$: cpu / gpu
