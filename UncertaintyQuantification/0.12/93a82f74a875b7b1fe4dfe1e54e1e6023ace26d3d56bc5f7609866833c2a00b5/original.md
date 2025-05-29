```
SubSetInfinity(n::Integer, target::Float64, levels::Integer, s::Real)
```

Defines the properties of a Subset-∞ simulation where `n` is the number of initial samples, `target` is the target probability of failure at each level, `levels` is the maximum number of levels and `s` is the standard deviation for the proposal samples.

# Examples

```jldoctest
julia> SubSetInfinity(100, 0.1, 10, 0.5)
SubSetInfinity(100, 0.1, 10, 0.5)
```

# References

[auRareEventSimulation2016](@cite)

[patelliEfficientMonteCarlo2015](@cite)
