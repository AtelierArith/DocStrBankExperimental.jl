```
multicompare(specs::AbstractArray{Spectrum{T}}) where {T <: Real}
```

Compares the intensity for the spectra in `specs` against the mean intensity on a channel-by-channel basis.  Compute the ratio for each channel in each  spectrum of the spectrum intensity over the mean intensity for that channel. You expect the ratio to be unity when the spectra are identical and deviate from unity when the spectra are different. 
