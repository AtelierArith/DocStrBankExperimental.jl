```
fitted_mean(gas::ScoreDrivenModel{D, T}, observations::Vector{T};
            initial_params::Matrix{T}=stationary_initial_params(gas)) where {D, T}
```

Returns the fitted mean of the in-sample series, i.e., the mean of the predictive distribution at each time step using the fitted parameters in `gas`.
