```
seisimageplot(d; <keyword arguments>);
seisimageplot!(ax, d; <keyword arguments>);
```

Recipe to plot time-space, color plot of 2D seismic data `d`.

# Arguments:

  * `d::Matrix{<:AbstractFloat}`: 2D seismic data to be plotted.

# Keyword Arguments:

  * `ox=0`: first point of x-axis.
  * `dx=1`: increment of x-axis.
  * `oy=0`: first point of y-axis.
  * `dy=1`: increment of y-axis.
  * `pclip=98`: percentile for determining clip.
  * `vmin=nothing`: minimum value used in colormapping data.
  * `vmax=nothing`: maximum value used in colormapping data.
  * `cmap=:seismic`: the colormap to be used.

# Examples

```julia
julia> d = SeisLinearEvents();
julia> f, ax, img = seisimageplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> img = seisimageplot!(ax, d)
```

Author: Firas Al Chalabi (2024) Credits: Aaron Stanton (2015)

  * Most of the code in this file is taken from SeisPlot.jl written by Aaron Stanton.
