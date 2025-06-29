```
SeisPlotAmplitude(d,fmax,dy ; <keyword arguments>)
```

Plot amplitude-frequency 2D seismic data `d`

# Arguments

  * `d::Array{Real,2}`: 2D data to plot.

# Keyword arguments

  * `fig=nothing`: the figure we want to plot on. If not supplied, one will be created and returned.
  * `ax=nothing`: the axis we want to plot on. If not supplied, one will be created and returned.
  * `fmax=100`: maximum frequency.
  * `dy=0.004`: time sample interval.
  * `normalize=false`: whether or not to normalize the data
  * `color=:red`: color of the plot.
  * `label=""`: plot label to be included in legend

# Example

```julia
julia> d = SeisLinearEvents();
julia> f, ax = SeisPlotAmplitude(d,100,0.004);
```

Author: Firas Al Chalabi (2024)
