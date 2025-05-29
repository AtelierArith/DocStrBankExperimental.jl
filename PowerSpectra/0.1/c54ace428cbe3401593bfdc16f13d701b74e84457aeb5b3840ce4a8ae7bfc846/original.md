```
CovField(name, maskT, maskP,
    σ²II::HealpixMap{T, O, AA}, σ²QQ::HealpixMap{T, O, AA}, σ²UU::HealpixMap{T, O, AA},
    beamT::SpectralVector{T}, beamP::SpectralVector{T})
```

Create a structure for describing the information needed for a covariance involving this field.

# Arguments:

  * `name::String`: name of this field
  * `maskT::HealpixMap{T}`: temperature mask
  * `maskP::HealpixMap{T}`: polarization mask
  * `σ²::PolarizedHealpixMap{T}`: pixel variances
  * `beamT::SpectralVector{T}`: temperature beam
  * `beamP::SpectralVector{T}`: polarization beam
