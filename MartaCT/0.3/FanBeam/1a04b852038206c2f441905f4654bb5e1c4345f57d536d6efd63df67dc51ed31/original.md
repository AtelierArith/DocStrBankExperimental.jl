```
fan2para(
    sinog_fan::AbstractMatrix{T},
    fbg::FanBeamGeometry;
    <keyword arguments>
) where {T} -> pbg, sinog_para
```

Convert given sinogram `sinog_fan` from fan beam geometry to parallel beam projections.

It is assumed that the detectors are arranged on a circle arc, not flat.

The function returns a tuple where `fbg` is the new geometry with fan beam projections parameters and `sinog_fan` is the converted sinogram.

# Arguments

  * `sinog_para`: the input sinogram.
  * `pbg`: the parallel geometry parameters.
  * `background=nothing`: background value to be used, defaults to 0.
  * `interpolation`: interpolation strategy; it should be a function   taking a matrix as input and returning a function of the indices to   get the interpolated value. By default it is a bilinear interpolation.

See Also: [`para2fan`](@ref)
