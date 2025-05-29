```
combine(uvals::Vector{AbstractUncertainValue}, weights::ProbabilityWeights; 
    n = 10000*length(uvals), 
    bw::Union{Nothing, Real} = nothing)
```

Combine multiple uncertain values into a single uncertain value. This is done by resampling each uncertain value in `uvals` proportionally to the provided  relative analytic `weights` indicating their relative importance (these are normalised by  default, so don't need to sum to 1), then pooling these draws together. Finally, a kernel  density estimate to the final distribution is computed over the `n` total draws.

Providing `ProbabilityWeights` leads to the exact same behaviour as for `AnalyticWeights`,  but may be more appropriote when, for example, weights have been determined  quantitatively. 

The KDE bandwidth is controlled by `bw`. By default, `bw = nothing`; in this case,  the bandwidth is determined using the `KernelDensity.default_bandwidth` function.

!!! tip
    For very wide, close-to-normal distributions, the default bandwidth may work well.  If you're combining very peaked distributions or discrete populations, however,  you may want to lower the bandwidth significantly.


# Example

```julia
v1 = UncertainValue(Normal, 1, 0.3)
v2 = UncertainValue(Normal, 0.8, 0.4)
v3 = UncertainValue([rand() for i = 1:3], [0.3, 0.3, 0.4])
v4 = UncertainValue(Normal, 3.7, 0.8)
uvals = [v1, v2, v3, v4];

# Two difference syntax options
combine(uvals, ProbabilityWeights([0.2, 0.1, 0.3, 0.2]))
combine(uvals, pweights([0.2, 0.1, 0.3, 0.2]), n = 20000) # adjust number of total draws
```
