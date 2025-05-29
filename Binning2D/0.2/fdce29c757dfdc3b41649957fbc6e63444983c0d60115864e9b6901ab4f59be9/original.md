```julia
nice_quantiles(xs, N; relative_threshold)

```

Make “nice” quantile boundaries from univariate data, using the following algorithm:

1. quantiles 1/(N+1), 2/(N+1), …, N/(N+1) are calculated
2. for quantiles which are closer than `(maximum(x) - minimum(x)) * relative_threshold`,

only one is kept

This algorithm is a heuristic designed for binning data that may pile up at various locations (edges etc).
