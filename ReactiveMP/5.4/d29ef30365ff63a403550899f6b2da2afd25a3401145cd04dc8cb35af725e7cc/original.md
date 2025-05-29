```
FullSampling <: CVISamplingStrategy
FullSampling(samples::Int = 10)
```

A sampling strategy that uses multiple samples drawn from distributions.

# Arguments

  * `samples::Int`: The number of samples to draw from each distribution. Default is 10.

# Example

```julia
# Use 100 samples for more accurate approximation
strategy = FullSampling(100)
```
