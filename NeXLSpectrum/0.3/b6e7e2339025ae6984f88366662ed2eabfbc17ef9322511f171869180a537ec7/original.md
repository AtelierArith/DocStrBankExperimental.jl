```
multimean(specs::Spectrum{T})::Spectrum{T} where {T <: Real}
```

Average on a channel-by-channel basis spectra collected from multiple detectors simultaneously from the same electrons interacting with the same material for  the real-time.  The detectors should be calibrated close to identically to maintain the detector resolution and peak positions.
