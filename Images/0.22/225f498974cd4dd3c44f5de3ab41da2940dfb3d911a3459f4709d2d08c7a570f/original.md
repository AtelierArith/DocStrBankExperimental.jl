```
corners = imcorner_subpixel(img; [method])
         -> Vector{HomogeneousPoint{Float64,3}}
corners = imcorner_subpixel(img, threshold, percentile; [method])
         -> Vector{HomogeneousPoint{Float64,3}}
```

Same as [`imcorner`](@ref), but estimates corners to sub-pixel precision.

Sub-pixel precision is achieved by interpolating the corner response values using the 4-connected neighbourhood of a maximum response value. See [`corner2subpixel`](@ref) for more details of the interpolation scheme.
