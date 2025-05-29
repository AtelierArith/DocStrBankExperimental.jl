```julia
sci_train(ann, data; ...)
sci_train(ann, data, θ; ...)
sci_train(
    ann,
    data,
    θ,
    opt,
    args;
    device,
    iters,
    ad,
    batch,
    shuffle,
    kwargs...
)

```

Scientific machine learning trainer

# Arguments

  * $ann$: neural network model
  * $data$: dataset
  * $θ$: parameters of neural network
  * $opt$: optimizer
  * $args$: rest arguments
  * $device$: cpu / gpu
  * $iters$: maximal iteration number
  * $ad$: automatical differentiation type
  * $batch$: batch size
  * $shuffle$: shuffle data (true) or not (false)
  * $kwargs$: rest keyword arguments
