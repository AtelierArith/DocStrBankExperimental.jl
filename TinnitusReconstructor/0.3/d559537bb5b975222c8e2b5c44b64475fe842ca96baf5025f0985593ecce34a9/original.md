```
spect2binnedrepr(s::BinnedStimgen, spect::AbstractVecOrMat{T}; n_bins::I = 0) where {BS<:BinnedStimgen,T,I<:Integer}
```

Convert a spectral representation into a binned representation.  The number of bins can be specified with the `n_bins` parameter.  `s.n_bins` is used by default.

Returns an `n_trials x n_bins` array containing the amplitude of the spectrum in each frequency bin,     where `n_trials` = size(binned_repr, 2).
