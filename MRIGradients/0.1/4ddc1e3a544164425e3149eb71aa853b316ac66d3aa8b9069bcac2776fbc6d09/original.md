```
GirfEssential(data::AbstractVecOrMat, vect::AbstractVector, isFreq::Bool, inChannels, outBasis)
```

Function to create a girf structure with the same interface as the constructor in the MATLAB implementation.

# Arguments

  * `data::AbstractVecOrMat` - [nSamples x nOutBasis x nInChannels] Full GIRF data.
  * `vect::AbstractVector` - [nSamples] Frequency vector indicating the frequency range, in unit of Hz.
  * `isFreq::Bool` - True for GIRF in frequency domain, false for GIRF in temporal domain.
  * `inChannels` - Input gradient and shim channel names.
  * `outBasis` - Output field basis.

# Outputs

  * g::GirfEssential - Constructed GirfEssential object.
