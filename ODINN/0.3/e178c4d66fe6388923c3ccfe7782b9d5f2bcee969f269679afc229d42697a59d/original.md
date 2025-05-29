```
function TrainingStats(;
    retcode::Union{String, Nothing} = nothing,
    losses::Vector{F} = Float64[],
    niter::I = 0
) where {F <: AbstractFloat, I <: Int}
```

Constructor for TrainingStats object used to store important information during training. 

# Arguments

  * `retcode`: Report code of the optimization.
  * `losses`: Vector storing the value of the loss function at each iteration.
  * `niter`: Total number of iterations/epochs.
  * `θ`: Parameters of neural network after training
