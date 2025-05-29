```
ShiftInvariantWaveletTransformObject(signal, wavelet)
```

Outer constructor and initialization of SIWT object.

# Arguments

  * `signal::Array{T} where T<:AbstractFloat`: Input signal.
  * `wavelet::OrthoFilter`: Wavelet filter.
  * `maxTransformLevel::S where S<:Integer`: (Default: `0`) Max transform level.
  * `maxShiftedTransformLevel::S where S<:Integer`: (Default: `0`) Max shifted transform levels.
