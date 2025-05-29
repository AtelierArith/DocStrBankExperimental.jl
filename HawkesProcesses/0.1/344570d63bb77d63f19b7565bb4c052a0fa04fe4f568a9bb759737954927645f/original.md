```
likelihood(events::Array{<:Number, 1}, background::Float64, kappa::Float64, kernel::Distributions.Distribution, maxT::Number)
```

Calculate the log likelihood of a Hawkes process for given parameters.

# Arguments

  * `events` Vector of events to calculate the likelihood for.
  * `background` Background rate.
  * `kappa` Kappa parameter.
  * `kernel` Function or distribution of the kernel.
  * `maxT` Maximum time of the process.

# Notes

  * The kernel function must be a proper probability distribution.

# Examples
