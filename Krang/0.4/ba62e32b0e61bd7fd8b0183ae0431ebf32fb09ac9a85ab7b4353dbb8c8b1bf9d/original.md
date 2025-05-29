```
SlowLightIntensityCamera(met::Kerr{T}, θo, αmin, αmax, βmin, βmax, res; A=Matrix) where {T}
```

Constructs a `SlowLightIntensityCamera` object.

# Arguments

  * `met::Kerr{T}`: The Kerr metric.
  * `θo`: The Observer's inclination angle. θo ∈ (0, π).
  * `αmin`: Minimum α coordinate on the screen.
  * `αmax`: Maximum α coordinate on the screen.
  * `βmin`: Minimum β coordinate on the screen.
  * `βmax`: Maximum β coordinate on the screen.
  * `res`: Resolution of the screen (number of pixels along one dimension).
  * `A`: Data type that stores screen pixel information (default is `Matrix`). A GPUMatrix can be used for GPU computations.

# Returns

  * A `SlowLightIntensityCamera` object.
