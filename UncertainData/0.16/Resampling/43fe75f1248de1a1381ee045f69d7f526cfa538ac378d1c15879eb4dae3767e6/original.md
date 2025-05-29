```
BinnedMeanWeightedResampling
```

Binned resampling where each bin is summarised using the mean of all draws  falling in that bin. Points in the dataset are sampled with probabilities according to `weights`.

## Fields

  * `left_bin_edges`. The left edgepoints of the bins. Either a range or some    custom type which implements `minimum` and `step` methods.
  * `weights`. The relative probability weights assigned to each point.
  * `n`. The total number of draws. These are distributed among the    points of the dataset according to `weights`.

## Examples

```julia
using UncertainData, StatsBase

# Resample on a grid from 0 to 200 in steps of 20
grid = 0:20:200

# Assume our dataset has 50 points. We'll assign random weights to them.
wts = Weights(rand(50))

# The total number of draws (on average 1000000/50 = 20000 draws per point
# if weights are equal)
n_draws = 10000000

# Create the resampling scheme
resampling = BinnedMeanWeightedResampling(grid, wts, n_draws)
```
