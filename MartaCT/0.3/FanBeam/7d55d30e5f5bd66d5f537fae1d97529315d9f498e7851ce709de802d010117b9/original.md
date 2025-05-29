```
para2fan(
    sinog_para::AbstractMatrix{T},
    fbg::FanBeamGeometry;
    <keyword arguments>
) where {T} -> fbg, sinog_fan
```

Convert given sinogram `sinog_para` from parallel beam geometry to fan beam projections.

The function returns a tuple where `fbg` is the new geometry with fan beam projections parameters and `sinog_fan` is the converted sinogram.

# Arguments

  * `sinog_para`: the input sinogram.
  * `pbg`: the geometry parameters.
  * `D`: focal spot to ISO distance.
  * `D′=nothing`: focal spot to detectors distance; if not specified   and also `γ` is not specified, is defined so that the total   fan angle is 1 radian.
  * `γ=nothing`: total fan angle in degrees.
  * `δ=1`: detectors spacing (cell size).
  * `background=nothing`: background value to be used, defaults to 0.
  * `interpolation`: interpolation strategy; it should be a function   taking a matrix as input and returning a function of the indices to   get the interpolated value. By default it is a bilinear interpolation.

See Also: [`fan2para`](@ref)
