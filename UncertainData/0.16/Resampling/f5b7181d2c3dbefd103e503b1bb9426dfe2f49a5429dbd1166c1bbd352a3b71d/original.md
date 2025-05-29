```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{UncertainScalarKDE}) -> UncertainIndexValueDataset
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{UncertainScalarPopulation}) -> UncertainIndexValueDataset
```

Resample every element of `x` the number of times given by `binning.n`. After resampling, distribute the values according to their indices, into the bins given by `binning.left_bin_edges`.

## Returns

Returns an `UncertainIndexValueDataset`. Indices are assumed to be uniformly distributed within each  bin, and are represented as `CertainValue`s at the bin centers. Values of the dataset have different  representations depending on what `binning` is:

  * If `binning isa BinnedResampling{UncertainScalarKDE}`, then values in each bin are represented by a    kernel density estimate to the distribution of the resampled values whose resampled indices    fall in that bin.
  * If `binning isa BinnedResampling{UncertainScalarPopulation}`, then values in each bin are    represented by equiprobable populations consisting of the resampled values whose resampled    indices fall in the bins.
