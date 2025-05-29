```
IdealCamera(n_pixels_x::Integer, n_pixels_y::Integer, pixel_size::T) where T<:Real
```

Construct an IdealCamera with square pixels directly from the number of pixels and pixel size.

# Arguments

  * `n_pixels_x::Integer`: Number of pixels in x dimension
  * `n_pixels_y::Integer`: Number of pixels in y dimension
  * `pixel_size::Real`: Size of pixels in microns

# Returns

IdealCamera{T} where T matches the type of pixel_size

# Example

```julia
# Create a 512x512 camera with 0.1 micron square pixels
cam = IdealCamera(512, 512, 0.1)

# Create with Float32 precision
cam32 = IdealCamera(512, 512, 0.1f0)
```
