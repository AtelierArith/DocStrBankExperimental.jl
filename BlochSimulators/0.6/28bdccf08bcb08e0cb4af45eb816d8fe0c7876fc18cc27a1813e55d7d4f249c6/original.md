```
Generic3D{T,V<:AbstractVector{Complex{T}},W<:AbstractVector{T},M<:AbstractMatrix{T},S} <: IsochromatSimulator{T}
```

Simulate a generic sequence defined by arrays containing RF and gradient waveforms. Unlike the Generic2D sequence, it is assumed that the excitation is homogenous over the voxel and therefore no summation over a slice direction is applied. The Δt vector stores the time intervals for the waveforms.

# Fields

  * `RF::V{Complex{T}}`: Vector with (complex) RF values during each time interval
  * `GR::M{T}`: Matrix with GRx, GRy and GRz values during each time interval
  * `sample::S`: Vector with Bool's to indicate the sample points
  * `Δt::V{T}`: Vector with time intervals
