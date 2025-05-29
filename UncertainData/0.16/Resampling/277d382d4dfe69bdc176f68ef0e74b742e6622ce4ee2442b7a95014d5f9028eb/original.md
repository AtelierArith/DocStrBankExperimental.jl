```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{RawValues}) -> Tuple(Vector, Vector{Vector})
```

Resample every element of `x` the number of times given by `binning.n`. After resampling, distribute the values according to their indices, into the `N` bins given by `binning.left_bin_edges`.

## Returns

Return a tuple containing the `N` different bin centers and a `N`-length vector of  resampled values whose resampled indices fall in the `N` different bins.

## Example

```julia
# Some example data with unevenly spaced time indices
npts = 300
time, vals = sort(rand(1:1000, npts)), rand(npts)

# Add uncertainties to indices and values, and represent as 
# UncertainIndexValueDataset 
utime = [UncertainValue(Normal, t, 10) for t in time]
uvals = [UncertainValue(Normal, v, 0.1) for v in vals]

udata = UncertainIndexValueDataset(utime, uvals)

# Bin data into fall in 25 time step wide time bins ranging 
# from time indices 100 to 900 and return a vector of raw 
# values for each bin. Do this by resampling each uncertain
# data point 10000 times and distributing those draws among 
# the bins.
left_bin_edges = 100:25:900
n_draws = 10000
binning = BinnedResampling(RawValues, left_bin_edges, n_draws)

bin_centers, bin_draws = bin(udata, binning)
```
