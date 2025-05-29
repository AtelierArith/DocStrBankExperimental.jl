```
plot_simage(image, spacing; perc=98, cmap=:linear_grey_10_95_c0_n256,
            o=(0, 0), interp="hanning", aspect=nothing, d_scale=1.5,
            labels=(:X, :Depth), name="RTM", units=(:m, :m), new_fig=true,
            save=nothing, cbar=false)
```

Plot a 2D seismic image with a grid spacing `spacing`. Calls [`_plot_with_units`](@ref).

# Arguments

  * `image::Array{T, 2}`: image to be plotted
  * `spacing::Tuple`: grid spacing in physical units
  * `perc::Int`: (Optional) Clipping percentile, default=95
  * `cmap::Symbol`: (Optional) Color map, default=:linear*grey*10*95*c0_n256
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
