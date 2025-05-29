```
combine(uvals::Vector{AbstractUncertainValue}, weights::FrequencyWeights;
    bw::Union{Nothing, Real} = nothing)
```

Combine multiple uncertain values into a single uncertain value. This is done by resampling each uncertain value in `uvals` according to their relative frequencies (the absolute number of draws provided by `weights`). Finally, a kernel density  estimate to the final distribution is computed over the `sum(weights)` total draws.

The KDE bandwidth is controlled by `bw`. By default, `bw = nothing`; in this case,  the bandwidth is determined using the `KernelDensity.default_bandwidth` function.

!!! tip
    For very wide and close-to-normal distributions, the default bandwidth may work well.  If you're combining very peaked distributions or discrete populations, however,  you may want to lower the bandwidth significantly.


# Example

```julia
v1 = UncertainValue(Normal, 1, 0.3)
v2 = UncertainValue(Normal, 0.8, 0.4)
v3 = UncertainValue([rand() for i = 1:3], [0.3, 0.3, 0.4])
v4 = UncertainValue(Normal, 3.7, 0.8)
uvals = [v1, v2, v3, v4];

# Two difference syntax options
combine(uvals, FrequencyWeights([100, 500, 343, 7000]))
combine(uvals, pweights([1410, 550, 223, 801]))
```
