```
IdealCamera{T} <: AbstractCamera
```

Represents an ideal camera with regularly spaced pixels defined by their edges in physical units (microns).

# Fields

  * `pixel_edges_x::Vector{T}`: Physical positions of pixel edges in x direction (microns)
  * `pixel_edges_y::Vector{T}`: Physical positions of pixel edges in y direction (microns)

The edges are computed from pixel centers, where pixel (1,1) is centered at  (pixel*size*x/2, pixel*size*y/2) in physical coordinates.
