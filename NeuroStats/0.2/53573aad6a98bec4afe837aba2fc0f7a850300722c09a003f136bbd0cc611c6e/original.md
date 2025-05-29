```
bootstrap_ci(s; <keyword arguments>)
```

Calculate Confidence Interval using bootstrapping.

# Arguments

  * `s::AbstractMatrix`: signal (time points × epochs)
  * `n1::Int64=3000`: number of stage 1 resamplings – number of samples in the resampled signal
  * `n2::Int64=1000`: number of stage 2 resamplings – number of samples sampled from the signal
  * `cl::Float64=0.95`: confidence level

# Returns

Named tuple containing:

  * `s_avg::Vector{Float64}`: averaged signal
  * `s_ci_l::Vector{Float64}`: lower bound of the confidence interval
  * `s_ci_h::Vector{Float64}`: upper bound of the confidence interval
