```
ParallelBeamGeometry([T=Float32]; <keyword arguments>) where {T}
```

Construct geometry for the simulation.

# Arguments

  * `nϕ`: number of projections.
  * `nd=nothing`: number of detectors. If not specified, same as `nϕ`.
  * `rows=nothing`: number of rows in the reconstructed image. If not specified, same as `nd`.
  * `cols=nothing`: number of columns in the reconstructed image. If not specified, same as `rows`.
  * `width=nothing`: alias for `cols`.
  * `height=nothing`: alias for `rows`.
  * `α=360`: scan angle in degrees.
  * `α₀=0`: starting scan angle in degrees.
  * `center=nothing`: virtual center channel, defaults to `(nd-1)/2`.
