```
binnedrepr2wav(s::BS, binned_repr::AbstractVecOrMat{T}; min_db::Real = -20) where {BS <: BinnedStimgen, I <: Integer, T <: Real}
```

Converts a binned representation to a waveform after rescaling to between `min_db` and 0.

Returns only the waveform.
