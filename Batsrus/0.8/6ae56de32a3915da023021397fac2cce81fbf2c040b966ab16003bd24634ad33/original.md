```
 interp2d(bd::BATS, var::AbstractString, plotrange=[-Inf, Inf, -Inf, Inf],
	 plotinterval=Inf; kwargs...)
```

Return 2D interpolated slices of data `var` from `bd`. If `plotrange` is not set, output data resolution is the same as the original.

# Keyword Arguments

  * `innermask=false`: Whether to mask the inner boundary with NaN.
  * `rbody=1.0`: Radius of the inner mask. Used when the rbody parameter is not found in the header.
  * `useMatplotlib=true`: Whether to Matplotlib (faster) or NaturalNeighbours for scattered interpolation. If true, a linear interpolation is performed on a constructed triangle mesh.
