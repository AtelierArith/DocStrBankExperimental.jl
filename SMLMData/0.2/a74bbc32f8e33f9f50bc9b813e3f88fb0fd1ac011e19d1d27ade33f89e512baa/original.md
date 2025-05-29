```
IdealCamera(pixel_centers_x::AbstractUnitRange, pixel_centers_y::AbstractUnitRange, pixel_size::T) where T<:Real
```

Construct an IdealCamera with square pixels given pixel center positions and a scalar pixel size.

# Arguments

  * `pixel_centers_x::AbstractUnitRange`: Range of pixel center indices in x (typically 1:N)
  * `pixel_centers_y::AbstractUnitRange`: Range of pixel center indices in y (typically 1:M)
  * `pixel_size::Real`: Size of pixels in microns

# Returns

IdealCamera{T} where T matches the type of pixel_size

# Type Parameters

  * `T`: Numeric type for all spatial measurements (e.g., Float64, Float32)

# Example

```julia
# Create a 512x512 camera with 0.1 micron square pixels
cam = IdealCamera(1:512, 1:512, 0.1)

# Create with Float32 precision
cam32 = IdealCamera(1:512, 1:512, 0.1f0)
```

Note: Pixel (1,1) is centered at (pixel*size/2, pixel*size/2) in physical coordinates.
