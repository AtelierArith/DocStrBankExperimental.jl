```
System([TF], surfaces; kwargs...)
```

Return an object of type `System` with pre-allocated storage for internal system variables

# Arguments:

  * `TF`: Floating point type, defaults to the floating point type used by `surface`
  * `surfaces`:      Either:       - One or more grids of shape (3, nc+1, ns+1) which represents lifting surfaces,       or       - One or more matrices of surface panels (see [`SurfacePanel`](@ref)) of         shape (nc, ns)      where `nc` is the number of chordwise panels and `ns` is the number of      spanwise panels

# Keyword Arguments

  * `nw`: Number of chordwise wake panels for each surface. Defaults to zero wake  panels on each surface
  * `grids`: Grids of the surfaces, represented by matrices of vertices
  * `ratios`: Ratios of the locations of each control point on each panel
  * `sections`: Section properties for each surface (Used as part of nonlinear VLM)
  * `invert_normals`: Flags indicating whether the normals of each surface should  be inverted
