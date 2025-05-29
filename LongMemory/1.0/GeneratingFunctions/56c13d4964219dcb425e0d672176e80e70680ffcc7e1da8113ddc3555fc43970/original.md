```
sds_gen(T::Int,d; t=0.5, μ=0, σ=1)
```

Generate a time series with long memory parameter `d` and length `T` using the stochastic duration shocks model.

# Arguments

  * `T::Int`: length of the time series
  * `d::Float64`: long memory parameter

# Optional arguments

  * `t::Float64`: taper length
  * `μ::Float64`: mean of the time series
  * `σ::Float64`: standard deviation of the time series

# Output

  * `x::Vector`: time series with long memory

# Notes

The taper length `t` is the proportion of the time series that is pre-sampled to avoid the initial bias of the model. Reference: Parke (1999)

# Examples

```julia-repl
julia> sds_gen(100,0.4)
```
