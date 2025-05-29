```
System(TF, nc, ns; nw = zero(nc))
```

Return an object of type `System` with pre-allocated storage for internal system variables

# Arguments:

  * `TF`: Floating point type.
  * `nc`: Number of chordwise panels on each surface.
  * `ns`: Number of spanwise panels on each surface.

# Keyword Arguments

  * `nw`: Number of chordwise wake panels for each surface. Defaults to zero wake  panels on each surface
  * `grids`: Grids of the surfaces, represented by matrices of vertices
  * `ratios`: Ratios of the locations of each control point on each panel
  * `sections`: Section properties for each surface (Used as part of nonlinear VLM)
  * `invert_normals`: Flags indicating whether the normals of each surface should  be inverted
