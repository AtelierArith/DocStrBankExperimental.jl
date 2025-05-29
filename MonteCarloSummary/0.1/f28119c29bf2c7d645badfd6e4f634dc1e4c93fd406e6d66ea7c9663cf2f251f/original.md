```
mcsummary(A::AbstractMatrix{<:Real}, p::NTuple{N, T}=(0.025, 0.25, 0.5, 0.75, 0.975);
          [dim::Integer=1], [multithreaded::Bool=true]) where {T<:Real, N}
```

Compute the summary of the Monte Carlo simulations, where the simulation index corresponds to dimension `dim` and `p` is the tuple of probabilities on the interval [0,1] corresponding to the quantile(s) of interest.

The summary consists of the mean, Monte Carlo standard error, standard deviation, and quantiles, concatenated into a matrix, in that order.
