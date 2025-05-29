```
caveats(n1, c::CWT{B,CT,W}; coiTolerance = exp(-2), fsample = 2000) -> sRange, meanFreqs, coi
```

Given a length `n1` and a CWT struct `c`, returns the scales `sRange` used, the mean frequencies of the wavelets `meanFreqs`, and the cone of influence `coi` for each wavelet. Returns the period, the scales, and the cone of influence for the given wavelet transform. If you have sampling information, you will need to scale the vector scale appropriately by 1/δt, and the actual transform by δt^(1/p).
