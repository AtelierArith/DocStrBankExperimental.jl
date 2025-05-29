```
randomize!(D::DeltaComplex; kwargs...) -> Int
```

Randomly flip edges in `D` until `D` is sufficiently generic and return the number of attempted flips.

The measure by which we determine if `D` is sufficiently generic is through its diameter. This Method repeatedly flips a certain number of times. After each flip sequence, the diameter is computed. Once this was repeated a certain number of times, the variance of all these past diameter measurements gets computed.

In theory, the variance should diminish over time. However, as we are flipping randomly, it will never truly converge to 0. A certain flutter in the variance is expected, this will at some point cause the variance to increase every so often. The algorithm stops once the last measured variance is bigger than the past few measurements.

# Arguments

  * `num_initial_flips::Integer=1000000` : the number of flips to do before even start taking measurements.
  * `num_flips_per_step::Integer=10000` : the number of flips to do before computing the diameter each step.
  * `variance_interval_size::Integer=10` : the number of diameters to store, before computing their variance.
  * `lookback_size::Integer=2` : how far back to compare the current variance to, in order to decide when to stop.

# Examples

```julia-repl
julia> D = deltacomplex(30,30);
julia> randomize!(D, num_initial_flips=10000, num_flips_per_step = 1000, variance_interval_size=10, lookback_size = 5)
160000
```
