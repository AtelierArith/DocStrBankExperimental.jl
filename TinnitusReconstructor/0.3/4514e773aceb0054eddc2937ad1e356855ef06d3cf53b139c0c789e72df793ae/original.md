```
binnedrepr2spect(s::BinnedStimgen, binned_repr::AbstractArray{T}) where {BS<:BinnedStimgen,T}
```

Convert the binned representation into a spectral representation.  The number of bins can be specified with the `n_bins` parameter.  `s.n_bins` is used by default.

Returns an `n_frequencies x n_trials` spectral array, where `n_trials` = size(binned_repr, 2).
