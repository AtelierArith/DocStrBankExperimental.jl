```
seisoverlayplot(d; <keyword arguments>)
seisoverlayplot!(ax, d; <keyword arguments>)
```

Recipe to plot time-space, overlay plot of 2D seismic data `d`.

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
  * `wiggle_fill_color=:black`: color for filling the positive wiggles.
  * `wiggle_line_color=:black`: color for wiggles' lines.
  * `wiggle_trace_increment=1`: increment for wiggle traces.
  * `xcur=1.2`: wiggle excursion in traces corresponding to clip.
  * `cmap=:seismic`: the colormap to be used.

# Examples

```julia
julia> d = SeisLinearEvents();
julia> f, ax, ov = seisoverlayplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> ov = seisoverlayplot!(ax, d)
```
