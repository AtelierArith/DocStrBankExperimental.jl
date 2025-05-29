```
bin(x::AbstractUncertainIndexValueDataset, 
    binning::BinnedWeightedResampling{RawValues}) -> Tuple(Vector, Vector{Vector})
```

Resample every element of `x` a number of times. After resampling, distribute the  values according to their indices, into the `N` bins given by the `N-1`-element  grid defined by `binning.left_bin_edges`. In total, `length(x)*binning.n` draws  are distributed among the bins. The precise number of times `x[i]` is resampled is  given by the `binning.weights[i]` (probability weights are always normalised to 1).

## Returns

Return a tuple containing the `N` different bin centers and a `N`-length vector of  resampled values whose resampled indices fall in the `N` different bins.

## Example

```julia
using Plots, UncertainData
# Some example data with unevenly spaced time indices
function ar1(n::Int, x0 = 0.5, p = 0.3)
    vals = zeros(n)
    [vals[i] = vals[i - 1]*p + rand()*0.5 for i = 2:n]
    return vals
end

npts = 50
time, vals = sort(rand(1:1000, npts)), ar1(npts)

# Add uncertainties to indices and values, and represent as 
# UncertainIndexValueDataset 
utime = [UncertainValue(Normal, t, 5) for t in time]
uvals = [UncertainValue(Normal, v, 0.03) for v in vals]

udata = UncertainIndexValueDataset(utime, uvals)

# Bin data into fall in 25 time step wide time bins ranging 
# from time indices 100 to 900 and return a vector of raw 
# values for each bin. Do this by resampling each uncertain
# data point on average 10000 times and distributing those 
# draws among the bins. 
time_grid = 100:40:900
n_draws = 5000
# Let odd-indexed values be three times as likely to be 
# sampled compared to even-indexed values.
wts = Weights([i % 2 == 0 ? 1 : 3 for i = 1:length(udata)])
binning = BinnedWeightedResampling(RawValues, time_grid, wts, n_draws)

bin_centers, bin_draws = bin(udata, binning);
```
