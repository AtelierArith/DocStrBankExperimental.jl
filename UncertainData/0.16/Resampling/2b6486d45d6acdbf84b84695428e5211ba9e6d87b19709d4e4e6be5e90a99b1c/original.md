```
resample(x::AbstractUncertainIndexValueDataset, resampling::BinnedMeanResampling)
```

Transform index-irregularly spaced uncertain data onto a regular index-grid and  take the mean of the values in each bin. 

Distributions in each index bin are obtained by resampling all index values in `x`  `resampling.n` times, and mapping those index draws to the bins. Simultaneously, the  values in `x` are resampled and placed in the corresponding bins. Finally, the mean  in each bin is calculated. In total, `length(x)*resampling.n` draws are distributed  among the bins to form the final mean estimate.

Returns a vector of mean values, one for each bin.

Assumes that the points in `x` are independent.

## Example

```julia
vars = (1, 2)
npts, tstep = 100, 10
d_xind = Uniform(2.5, 15.5)
d_yind = Uniform(2.5, 15.5)
d_xval = Uniform(0.01, 0.2)
d_yval = Uniform(0.01, 0.2)

X, Y = example_uncertain_indexvalue_datasets(ar1_unidir(c_xy = 0.5), npts, vars, tstep = tstep,
    d_xind = d_xind, d_yind = d_yind,
    d_xval = d_xval, d_yval = d_yval);

n_draws = 10000 # draws per uncertain value
time_grid = 0:50:1000

# Resample both X and Y so that they are both at the same time indices, 
# and take the mean of each bin.
resampled_dataset = resample(X, BinnedMeanResampling(time_grid, n_draws))
resampled_dataset = resample(Y, BinnedMeanResampling(time_grid, n_draws))
```
