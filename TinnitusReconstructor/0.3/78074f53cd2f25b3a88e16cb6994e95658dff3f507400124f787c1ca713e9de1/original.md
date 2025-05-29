```
binnedrepr2wav(s::BS, binned_repr::AbstractVecOrMat{T}, mult, binrange,
new_n_bins::I = 256) where {BS <: BinnedStimgen, I <: Integer, T <: Real}
```

Converts a binned representation into a waveform  by enhancing the resolution (to `new_n_bins`) via interpolation,  sharpening the peaks (`mult`), and rescaling the dynamic range (`binrange`).

Returns a waveform and the associated frequency spectrum.
