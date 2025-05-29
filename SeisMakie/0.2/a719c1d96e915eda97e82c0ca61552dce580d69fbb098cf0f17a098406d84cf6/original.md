```
seisamplitudeplot(d; <keyword arguments>)
seisamplitudeplot!(ax, d; <keyword arguments>)
```

Plot amplitude-frequency 2D seismic data `d`.

# Arguments

  * `d::Array{Real,2}`: 2D data to plot.

# Keyword arguments

  * `fmax=100`: maximum frequency.
  * `dy=0.004`: time sample interval.
  * `normalize=false`: whether or not to normalize the data
  * `color=:black`: color of the plot.
  * `label=""`: plot label to be included in legend

# Examples

```julia
julia> d = SeisLinearEvents();
julia> f, ax, amp = seisamplitudeplot(d)
```

```julia
julia> d = SeisLinearEvents(); f = Figure(); ax = Axis(f)
julia> amp = seisamplitudeplot!(ax, d)
```

Author: Firas Al Chalabi (2024) Credits: Aaron Stanton (2015)

  * Most of the code in this file is taken from SeisPlot.jl written by Aaron Stanton.
