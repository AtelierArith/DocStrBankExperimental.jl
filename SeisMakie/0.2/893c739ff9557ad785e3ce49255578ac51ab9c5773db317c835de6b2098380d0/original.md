```
SeisDifference(d1, d2; <keyword arguments>)
```

Plot time-space, 2D seismic data `d1`, `d2`, and their difference (`d1 - d2`) with color, wiggles or overlay. The plots are arranged horizontally by default.

# Arguments:

  * `d1::Matrix{<:AbstractFloat}`: the measured seismic traces. Number of columns corresponds to number                                of traces whereas number of rows corresponds to the number of times                                amplitude was measured for each trace
  * `d2::Matrix{<:AbstractFloat}`: same description as d1.

# Keyword Arguments:

  * `fig=nothing`: the figure we want to plot on. If not supplied, one will be created and returned.
  * `gx::Vector{<:Real}=nothing`: the real coordinates of the seismometers corresponding to the traces in d
  * `ox=0`: first point of x-axis.
  * `dx=1`: increment of x-axis.
  * `oy=0`: first point of y-axis.
  * `dy=1`: increment of y-axis.
  * `pclip=98`: percentile for determining clip.
  * `vmin=nothing`: minimum value used in colormapping data.
  * `vmax=nothing`: maximum value used in colormapping data.
  * `wiggle_fill_color=:black`: color for filling the positive wiggles.
  * `wiggle_line_color=:black`: color for wiggles' lines.
  * `wiggle_trace_increment=1`: increment for wiggle traces.
  * `xcur=1.2`: wiggle excursion in traces corresponding to clip.
  * `cmap=:viridis`: the colormap to be used for color and overlay plots.
  * `style`: determines the type of plot. Can be either "wiggle"/"wiggles", "color", "overlay".
  * `horizontal=true`: if set to false, d1, d2, and their difference are arranged vertically.

Return the figure and 3 axes corresponding to d1, d2, d1-d2.

# Example

```julia
julia> d1 = SeisLinearEvents(); d2 = SeisLinearEvents();
julia> f, ax1, ax2, ax_diff = SeisDifference(d1, d2);
```

Author: Firas Al Chalabi (2024)
