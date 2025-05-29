```
SequentialMonteCarlo(;
    samples::Int=10_000,
    seed::Integer=rand(UInt64),
    verbose::Bool=false,
    threaded::Bool=true
)
```

Sequential Monte Carlo simulation parameters for PRAS analysis

It it recommended that you fix the random seed for reproducibility.

# Arguments

  * `samples::Int=10_000`: Number of samples
  * `seed::Integer=rand(UInt64)`: Random seed
  * `verbose::Bool=false`: Print progress
  * `threaded::Bool=true`: Use multi-threading

# Returns

  * `SequentialMonteCarlo`: PRAS simulation specification
