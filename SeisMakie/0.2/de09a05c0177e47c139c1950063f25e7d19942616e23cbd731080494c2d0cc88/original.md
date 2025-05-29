```
seisfkplot(d; <keyword arguments>)
seisfkplot!(ax, d; <keyword arguments>)
```

Plot frequency-wavenumber 2D seismic data `d`.

# Arguments

  * `d::Matrix{<:AbstractFloat}`: 2D data to plot.

# Keyword arguments:

  * `fig=nothing`: the figure we want to plot on. If not supplied, one will be created and returned.
  * `pclip=99.9`: percentile for determining clip.
  * `vmin=nothing`: minimum value used in colormapping data.
  * `vmax=nothing`: maximum value used in colormapping data.
  * `fmax=100`: maximum frequency for `"FK"` or `"Amplitude"` plot.
  * `dx=1`: increment of x-axis.
  * `dy=1`: increment of y-axis.
  * `cmap=:PuOr`: colormap

Return the figure and axis corresponding to d.

# Examples

```julia
julia> d = SeisLinearEvents();
julia> f, ax, fk = seisfkplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> fk = seisfkplot!(ax, d)
```

Author: Firas Al Chalabi (2024) Credits: Aaron Stanton (2015)

  * Most of the code in this file is taken from SeisPlot.jl written by Aaron Stanton.
