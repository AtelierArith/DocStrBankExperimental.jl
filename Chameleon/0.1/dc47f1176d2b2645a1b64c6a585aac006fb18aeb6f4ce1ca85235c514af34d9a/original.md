```
distinct_colors(
    n_colors::Integer;
    minimal_saturation::Real=33,
    minimal_lightness::Real=20,
    maximal_lightness::Real=80
)::Tuple{AbstractVector{<:AbstractString}, AbstractMatrix{<:Real}}
```

Pick a number of distinct colors.

This ensures all colors are distinct by packing the (visible part) of the CIELAB color space with the needed number of spheres, and using their centers to generate the colors.

# Arguments

  * `n_colors`: The requested (positive) number of colors.
  * `minimal_saturation`: Exclude colors whose saturation (hypot(a, b) in CIELAB color space) is less than this value.
  * `minimal_lightness`: Exclude colors whose lightness (l in CIELAB color space) is less than this value.
  * `maximal_lightness=80`: Exclude colors whose lightness (l in CIELAB color space) is more than this value.

# Returns

A tuple with two elements, a vector of color names and a matrix of the `lab` coordinates of the colors (rows are `l`, `a` and `b`, columns are colors). Colors are named in the usual `#RRGGBB` hexadecimal format.
