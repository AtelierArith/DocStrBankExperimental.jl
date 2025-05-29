```
IdealCamera(pixel_centers_x::AbstractUnitRange, pixel_centers_y::AbstractUnitRange, 
            pixel_size::Tuple{T, T}) where T<:Real
```

Construct an IdealCamera with rectangular pixels given pixel center positions and x,y pixel sizes.

# Arguments

  * `pixel_centers_x::AbstractUnitRange`: Range of pixel center indices in x (typically 1:N)
  * `pixel_centers_y::AbstractUnitRange`: Range of pixel center indices in y (typically 1:M)
  * `pixel_size::Tuple{T, T}`: Tuple of (x*size, y*size) in microns

# Returns

IdealCamera{T} where T matches the type of the pixel sizes

# Type Parameters

  * `T`: Numeric type for all spatial measurements (e.g., Float64, Float32)

# Example

```julia
# Create a 512x256 camera with rectangular pixels (0.1 x 0.15 microns)
cam = IdealCamera(1:512, 1:256, (0.1, 0.15))

# Create with Float32 precision
cam32 = IdealCamera(1:512, 1:256, (0.1f0, 0.15f0))
```

Note: Pixel (1,1) is centered at (pixel*size[1]/2, pixel*size[2]/2) in physical coordinates.
