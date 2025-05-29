```
BinnedWeightedResampling(left_bin_edges, weights, n::Int; bin_repr = UncertainScalarKDE)
BinnedWeightedResampling(UncertainScalarKDE, left_bin_edges, weights, n::Int)
BinnedWeightedResampling(UncertainScalarPopulation, left_bin_edges, weights, n::Int)
BinnedWeightedResampling(RawValues, left_bin_edges, weights, n::Int)
```

Indicates that binned resampling should be performed, but weighting each point in the dataset differently.

## Fields

  * `left_bin_edges`. The left edgepoints of the bins. Either a range or some    custom type which implements `minimum` and `step` methods.
  * `weights`. The relative probability weights assigned to each point.
  * `n`. The total number of draws. These are distributed among the    points of the dataset according to `weights`.
  * `bin_repr`. A type of uncertain value indicating how each bin should be    summarised (`UncertainScalarKDE` for kernel density estimated distributions   in each bin, `UncertainScalarPopulation` to represent values in each bin    as an equiprobable population) or not summarise but return raw values    falling in each bin (`RawValues`).

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

# Create the resampling scheme. Use kernel density estimates to distribution 
# in each bin.
resampling = BinnedWeightedResampling(grid, wts, n_draws, bin_repr = UncertainScalarKDE)

# Represent each bin as an equiprobably population 
resampling = BinnedWeightedResampling(grid, wts, n_draws, bin_repr = UncertainScalarPopulation)

# Keep raw values for each bin (essentially the same as UncertainScalarPopulation,
# but avoids storing an additional vector of weights for the population members).
resampling = BinnedWeightedResampling(grid, wts n_draws, bin_repr = RawValues)
```
