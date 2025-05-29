```
bootstrap_stat(s; <keyword arguments>)
```

Calculate signal statistic using bootstrapping.

# Arguments

  * `s::AbstractMatrix`: signal (time points × epochs)
  * `n1::Int64=3000`: number of stage 1 resamplings – number of samples in the resampled signal
  * `n2::Int64=1000`: number of stage 2 resamplings – number of samples sampled from the signal
  * `f::String`: statistic function to be applied, e.g. `f="abs(maximum(obj))"; signal is given using variable`obj` here.

# Returns

  * `out::AbstractVector`
