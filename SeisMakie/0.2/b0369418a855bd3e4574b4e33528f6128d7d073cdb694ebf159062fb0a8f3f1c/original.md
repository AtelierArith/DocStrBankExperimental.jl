```
seiswiggleplot(d; <keyword arguments>)
seiswiggleplot!(ax, d; <keyword arguments>)
```

Recipe to plot time-space, wiggle plot of 2D seismic data `d`.

# Arguments:

  * `d::Matrix{<:AbstractFloat}`: the measured seismic traces. Number of columns corresponds to number                               of traces whereas number of rows corresponds to the number of times                               amplitude was measured for each trace

# Keyword Arguments:

  * `gx::Vector{<:Real}=nothing`: the real coordinates of the seismometers corresponding to the traces in d
  * `ox=0`: first point of x-axis.
  * `dx=1`: increment of x-axis.
  * `oy=0`: first point of y-axis.
  * `dy=1`: increment of y-axis.
  * `wiggle_fill_color=:black`: color for filling the positive wiggles.
  * `wiggle_line_color=:black`: color for wiggles' lines.
  * `wiggle_trace_increment=1`: increment for wiggle traces.
  * `xcur=1.2`: wiggle excursion in traces.

# Examples

```julia
julia> d = SeisLinearEvents();
julia> f, ax, wp = seiswiggleplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> wp = seiswiggleplot!(ax, d)
```

**Note: animations only work with this recipe if you update the observable `d`  with a matrix of the same size.**

Author: Firas Al Chalabi (2024) Credits: Aaron Stanton (2015) 

  * The code in this file was inspired by some of Aaron Stanton's in SeisPlot.jl.
