```julia
get_lims(x) -> Tuple{Any, Any}
get_lims(x, n) -> Tuple{Any, Any}

```

Get approximate lower and upper limits of a field `x` based on the mean and standard deviation ($\mu \pm n \sigma$). If `x` is constant, a margin of `1e-4` is enforced. This is required for contour plotting functions that require a certain range.
