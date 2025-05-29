```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedWeightedResampling{UncertainScalarKDE}) -> UncertainIndexValueDataset
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedWeightedResampling{UncertainScalarPopulation}) -> UncertainIndexValueDataset
```

Resample every element of `x` a number of times. After resampling, distribute the  values according to their indices, into the `N` bins given by the `N-1`-element  grid defined by `binning.left_bin_edges`. In total, `length(x)*binning.n` draws  are distributed among the bins. The precise number of times `x[i]` is resampled is  given by `binning.weights[i]` (probability weights are always normalised to 1).

## Returns

Returns an `UncertainIndexValueDataset`. Indices are assumed to be uniformly distributed within each  bin, and are represented as `CertainValue`s at the bin centers. Values of the dataset have different  representations depending on what `binning` is:

  * If `binning isa BinnedWeightedResampling{UncertainScalarKDE}`, then values in each bin are    represented by a kernel density estimate to the distribution of the resampled values whose    resampled indices fall in that bin.
  * If `binning isa BinnedWeightedResampling{UncertainScalarPopulation}`, then values in each bin are    represented by equiprobable populations consisting of the resampled values whose resampled    indices fall in the bins.
