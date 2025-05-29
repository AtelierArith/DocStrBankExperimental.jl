```
Generic2D{T,V,M,S} where {T<:AbstractFloat, V<:AbstractVector, M<:AbstractMatrix, S} <: IsochromatSimulator{T}
```

Simulate a generic 2D sequence defined by arrays containing RF and gradient waveforms. Contains a loop over z locations to take into account slice profile effects. The Δt vector stores the time intervals for the waveforms.

# Fields

  * `RF::V{Complex{T}}`: Vector with (complex) RF values during each time interval
  * `GR::M{T}`: Matrix with GRx, GRy and GRz values during each time interval
  * `sample::S`: Vector with Bool's to indicate the sample points
  * `Δt::V{T}`: Vector with time intervals
  * `z::V{T}`: Vector with different positions along the slice direction
