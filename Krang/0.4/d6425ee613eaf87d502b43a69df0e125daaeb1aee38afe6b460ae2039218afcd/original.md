```
IntensityCamera(met::Kerr{T}, θo, αmin, αmax, βmin, βmax, res::Int; A=Matrix) where {T}
```

Constructor for an Intensity Camera.

# Arguments

  * `met::Kerr{T}`: The Kerr metric.
  * `θo`: Observer's inclination angle. θo ∈ (0, π).
  * `αmin`: Minimum value of α.
  * `αmax`: Maximum value of α.
  * `βmin`: Minimum value of β.
  * `βmax`: Maximum value of β.
  * `res::Int`: Resolution of the screen.
  * `A=Matrix`: Optional argument to specify the type of matrix to use. A GPUMatrix can be used for GPU computations.

# Returns

  * `IntensityCamera{T, A}`: An intensity camera object.
