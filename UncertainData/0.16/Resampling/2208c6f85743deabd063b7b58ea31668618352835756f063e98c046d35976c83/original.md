```
resample(x::AbstractUncertainIndexValueDataset, resampling::BinnedResampling{UncertainScalarKDE};
    bin_repr::Symbol = :kde, nan_threshold = 0.0)
```

Transform index-irregularly spaced uncertain data onto a regular index-grid. Distributions in each index bin are obtained by resampling all index values  in `x` `resampling.n` times, and mapping those index draws to the bins.  Simultaneously, the values in `x` are resampled and placed in the corresponding bins. In total, `length(x)*resampling.n` draws are distributed among the bins to form  the final KDEs.

Returns an `UncertainIndexValueDataset`. The distribution of values in the `i`-th bin  is approximated by a kernel density estimate (KDE) over the draws falling in the  `i`-th bin.

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
resampling = BinnedResampling(time_grid, n_draws)

# Resample both X and Y so that they are both at the same time indices.
resampled_dataset = resample(X, resampling)
resampled_dataset = resample(Y, resampling)
```
