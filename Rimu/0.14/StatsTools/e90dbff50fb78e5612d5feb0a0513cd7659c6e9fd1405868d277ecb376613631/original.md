```
mean_and_se(v::AbstractVector; α = 0.01, corrected::Bool=true, skip=0) -> mean, err
mean_and_se(r::BlockingResult) -> mean, err
```

Return the mean and standard error (as a tuple) of a time series obtained from [`blocking_analysis`](@ref). See also [`BlockingResult`](@ref).
