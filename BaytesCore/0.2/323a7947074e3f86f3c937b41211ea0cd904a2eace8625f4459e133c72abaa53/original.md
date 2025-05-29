```julia
mutable struct ChainsTune
```

Holds tuning information for number of chains in comparison to data.

# Fields

  * `coverage::Float64`: Proposed coverage of number of chains/number of data points.
  * `threshold::Float64`: Threshold for resampling, between 0.0 and 1.0.
  * `Nchains::Int64`: Number of chains.
  * `Ndata::Int64`: Number of data points.
