```
BinnedMeanResampling
```

Binned resampling where each bin is summarised using  the mean of all draws falling in that bin.

## Fields

  * `left_bin_edges`. The left edgepoints of the bins. Either a range or some    custom type which implements `minimum` and `step` methods.
  * `n`. The number of draws. Each point in the dataset is sampled `n` times.   If there are `m` points in the dataset, then the total number of draws    is `n*m`.

## Examples

```julia
using UncertainData

# Resample on a grid from 0 to 200 in steps of 20
grid = 0:20:200

# The number of samples per point in the dataset
n_draws = 10000

# Create the resampling scheme
resampling = BinnedMeanResampling(grid, n_draws)
```
