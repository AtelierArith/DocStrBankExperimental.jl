```
scalar_normalizer(;weights = OnlineStats.EqualWeight())
```

Returns preconfigured normalizer for scalar traces such as rewards. By default, all samples  have equal weights in the computation of the moments. See the [OnlineStats documentation](https://joshday.github.io/OnlineStats.jl/stable/weights/)  to use variants such as exponential weights to favor the most recent observations.
