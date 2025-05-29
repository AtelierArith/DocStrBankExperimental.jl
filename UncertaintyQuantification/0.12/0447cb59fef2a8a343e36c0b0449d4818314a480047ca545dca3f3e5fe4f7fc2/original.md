```
SubSetSimulation(n::Integer, target::Float64, levels::Integer, proposal::UnivariateDistribution)
```

Defines the properties of a Subset simulation where `n` is the number of initial samples, `target` is the target probability of failure at each level, `levels` is the maximum number of levels and `proposal` is the proposal distribution for the markov chain monte carlo.

# Examples

```jldoctest
julia> SubSetSimulation(100, 0.1, 10, Uniform(-0.2, 0.2))
SubSetSimulation(100, 0.1, 10, Uniform{Float64}(a=-0.2, b=0.2))
```

# References

[auEstimationSmallFailure2001](@cite)
