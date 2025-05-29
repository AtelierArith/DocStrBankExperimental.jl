```
array_normalizer(size::Tuple{Int}; weights = OnlineStats.EqualWeight())
```

Returns preconfigured normalizer for array traces such as vector or matrix states.  `size` is a tuple containing the dimension sizes of a state. E.g. `(10,)` for a 10-elements vector, or `(252,252)` for a square image. By default, all samples have equal weights in the computation of the moments. See the [OnlineStats documentation](https://joshday.github.io/OnlineStats.jl/stable/weights/)  to use variants such as exponential weights to favor the most recent observations.
