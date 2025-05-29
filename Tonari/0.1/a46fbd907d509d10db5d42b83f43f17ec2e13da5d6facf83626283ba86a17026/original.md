```
fill_gaps(rng::AbstractRNG, t::Vector{Float64}, x::Vector{Float64}, σₓ = nothing; randomise_values::Bool = true, poisson::Bool = true)
```

Fill gaps in a time series data with linear interpolation. If `randomise_values = true`, the interpolated values are drawn from a normal distribution with the mean and standard deviation of the data. If `poisson = true`, the interpolated values are drawn from a Poisson distribution with the mean of the data.

# Arguments

  * `rng::AbstractRNG`: random number generator
  * `t::Vector{Float64}`: time array
  * `x::Vector{Float64}`: data array
  * `σₓ`::Vector{Float64}: standard deviation of the data array (optional)
  * `randomise_values::Bool`: whether to randomise the interpolated values
  * `poisson::Bool`: whether to use a Poisson distribution for the interpolated values, this assumes that the data is in counts/dt
