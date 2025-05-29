```
localgeary(x, W)
```

Compute the Local Geary test of spatial autocorrelation.

# Optional Arguments

  * `permutations=9999`: number of permutations for the randomization test.
  * `rng=default_rng()`: random number generator for the randomization test.
  * `corrected=true`: divide the scaling factor by $n-1$ instead of $n$.
  * `categories=:positivenegative`: assing observations to positive or negative spatial autocorrelation, or in combination with the `:moran` scatterplot.
