```
FanBeamGeometry([T=Float32]; <keyword arguments>) where {T}
```

Create a new FanBeamGeometry object with given parameters.

It is assumed that the detectors are arranged on a circle arc, not flat.

# Arguments

  * `nϕ: number of scan angles.
  * `nd=nothing`: number of detectors.
  * `rows=nothing`: number of rows in the reconstructed image.
  * `cols=nothing`: number of columns in the reconstructed image.
  * `width=nothing`: alias for `cols`.
  * `height=nothing`: alias for `rows`.
  * `D`: focal spot to ISO distance.
  * `D′=nothing`: focal spot to detectors distance; if not specified   and also `γ` is not specified, is defined so that the total   fan angle is 1 radian.
  * `γ=nothing`: total fan angle in degrees.
  * `δ=1`: detectors spacing (cell size).
  * `α=360`: scan angle in degrees.
  * `α₀=0`: scan starting angle in degrees.
  * `center=nothing`: virtual center channel, defaults to `(nd-1)/2`.
