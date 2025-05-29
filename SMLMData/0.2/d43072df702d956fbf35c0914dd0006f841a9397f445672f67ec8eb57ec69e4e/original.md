```
AbstractCamera
```

Abstract base type for all camera implementations in single molecule localization microscopy (SMLM).

# Interface Requirements

Any concrete subtype of AbstractCamera must provide:

1. Field Requirements:

      * `pixel_edges_x::Vector{<:Real}`: Vector of pixel edge positions in x direction
      * `pixel_edges_y::Vector{<:Real}`: Vector of pixel edge positions in y direction
2. Units:

      * All edge positions must be in physical units (microns)
      * Origin (0,0) corresponds to the top-left corner of the camera
      * For a camera with N×M pixels, there will be N+1 x-edges and M+1 y-edges
3. Coordinate Convention:

      * Pixel (1,1) is centered at (pixel*size*x/2, pixel*size*y/2) microns
      * Edge positions define the boundaries of pixels in physical space
      * First edge position corresponds to the left/top edge of the first pixel
      * Last edge position corresponds to the right/bottom edge of the last pixel

# Notes

  * Edge positions must be monotonically increasing
  * The number of edges must be one more than the number of pixels in each dimension
  * While pixels are typically uniform in size, this is not a requirement of the interface
