```
IdealCamera(n_pixels_x::Integer, n_pixels_y::Integer, pixel_size::Tuple{T, T}) where T<:Real
```

Construct an IdealCamera with rectangular pixels directly from the number of pixels and x,y pixel sizes.

# Arguments

  * `n_pixels_x::Integer`: Number of pixels in x dimension
  * `n_pixels_y::Integer`: Number of pixels in y dimension
  * `pixel_size::Tuple{T, T}`: Tuple of (x*size, y*size) in microns

# Returns

IdealCamera{T} where T matches the type of the pixel sizes

# Example

```julia
# Create a 512x256 camera with rectangular pixels (0.1 x 0.15 microns)
cam = IdealCamera(512, 256, (0.1, 0.15))

# Create with Float32 precision
cam32 = IdealCamera(512, 256, (0.1f0, 0.15f0))
```
