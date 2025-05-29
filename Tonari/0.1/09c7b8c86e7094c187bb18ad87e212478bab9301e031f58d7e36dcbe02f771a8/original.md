```
sample(rng, sim, n=1, input_mean=0; σₓ = nothing, split_long=false, randomise_values=true, Fvar=nothing, alt=false, poisson=false, exponentiate=false, error_size=0.02)
```

Generate a time series with a given power spectral density (PSD) using the [1995A&A...300..707T](@cite) method.

# Arguments

  * `rng::MersenneTwister`: Random number generator.
  * `sim::Simulation`: The simulation
  * `n::Int`: Number of time series to generate. Default is 1.
  * `input_mean::Real`: The mean of the time series. Default is 0.
  * `σₓ::Array{Float64, 1}`: The errorbars of the time series. Default is nothing.
  * `split_long::Bool`: If true, the time series is split into shorter time series given by `sim.S_low`-1. Default is true.
  * `randomise_values::Bool`: If true, the values of the time series are randomised. Default is true.
  * `Fvar::Real`: The variance of the time series. Default is nothing.
  * `alt::Bool`: If true, uses the alternative Timmer & Koenig method. Default is false.
  * `poisson::Bool`: If true, Poisson noise is added to the time series. Default is false.
  * `exponentiate::Bool`: If true, the time series is exponentiated. Default is false.
  * `error_size::Real`: The size of the error. Default is 0.05.
