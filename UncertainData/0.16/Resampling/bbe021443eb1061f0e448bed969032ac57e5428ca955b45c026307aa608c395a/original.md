```
BinnedResampling(left_bin_edges, n::Int; bin_repr = UncertainScalarKDE)
BinnedResampling(UncertainScalarKDE, left_bin_edges, n::Int)
BinnedResampling(UncertainScalarPopulation, left_bin_edges, n::Int)
BinnedResampling(RawValues, left_bin_edges, n::Int)
```

Indicates that binned resampling should be performed.

## Fields

  * `left_bin_edges`. The left edgepoints of the bins. Either a range or some    custom type which implements `minimum` and `step` methods.
  * `n`. The number of draws. Each point in the dataset is sampled `n` times.   If there are `m` points in the dataset, then the total number of draws    is `n*m`.
  * `bin_repr`. A type of uncertain value indicating how each bin should be    summarised (`UncertainScalarKDE` for kernel density estimated distributions   in each bin, `UncertainScalarPopulation` to represent values in each bin    as an equiprobable population) or not summarise but return raw values    falling in each bin (`RawValues`).

## Examples

```julia
using UncertainData

# Resample on a grid from 0 to 200 in steps of 20
grid = 0:20:200

# The number of samples per point in the dataset
n_draws = 10000

# Create the resampling scheme. Use kernel density estimates to distribution 
# in each bin.
resampling = BinnedResampling(grid, n_draws, bin_repr = UncertainScalarKDE)

# Represent each bin as an equiprobably population 
resampling = BinnedResampling(grid, n_draws, bin_repr = UncertainScalarPopulation)

# Keep raw values for each bin (essentially the same as UncertainScalarPopulation,
# but avoids storing an additional vector of weights for the population members).
resampling = BinnedResampling(grid, n_draws, bin_repr = RawValues)
```
