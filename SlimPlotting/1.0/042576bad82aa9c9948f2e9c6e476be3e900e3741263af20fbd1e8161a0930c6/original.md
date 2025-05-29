```
compare_shots(image1, image2, spacing; perc=98, cmap=:linear_grey_10_95_c0_n256,
              o=(0, 0), interp="hanning", aspect=nothing, d_scale=1.5, side_by_side=false,
              chunksize=20, name="Data match", units="m", new_fig=true, save=nothing)
```

Compares the two shot records image1 and image2. This plotting utility supports two modes: `side_by_side` that plot the shot records next two each other with the second one having its traces reversed , and `overlap` (default) where the two shots are overlapped selecting `chunksize` (Default 20) traces from each shot alternatively.

# Arguments

  * `image1::Array{T, 2}`: First image
  * `image2::Array{T, 2}`: Second image to comapre against the first image
  * `spacing::Tuple`: grid spacing in physical units
  * `perc::Int`: (Optional) Clipping percentile, default=95
  * `cmap::Symbol`: (Optional) Color map, default=:linear*grey*10*95*c0_n256. Can provide a tuple of colormap for the `overlap` mode
  * `o::Tuple`: (Optional) Origin of the image, default=(0, 0)
  * `interp::String`: (Optional) Interpolation method, default="hanning"
  * `aspect::Symbol`: (Optional) Aspect ratio, default=:auto
  * `d_scale::Float`: (Optional) Depth scaling, default=1.5. Applied scaling is `(1:max_depth).^d_scale`.
  * `labels::Tuple`: (Optional) Labels for the axes, default=(:X, :Depth)
  * `name::String`: (Optional) Figure title, default="RTM"
  * `units::Tuple(String)`: (Optional) Physical units of each axis, default=(:m, :m).
  * `new_fig::Bool`: (Optional) Create a new figure, default=true
  * `save::String`: (Optional) Save figure to file, default=nothing doesn't save the figure
  * `cbar::Bool`: (Optional) Show colorbar, default=false
  * `chunksize::Integer`: Numberof trace in the chunk for the overlap comparison
  * `side_by_side::Bool`: Whether to plot a side-by-side (true) or overlap (false, default) comaprison
