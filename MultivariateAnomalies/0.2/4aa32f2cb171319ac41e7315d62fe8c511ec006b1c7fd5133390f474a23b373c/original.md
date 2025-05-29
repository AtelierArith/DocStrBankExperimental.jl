```
get_MedianCycles(datacube, cycle_length::Int = 46)
```

returns the median annual cycle of a datacube, given the length of the annual cycle (presetting: `cycle_length = 46`). The datacube can be 2, 3, 4-dimensional, time is stored along the first dimension.

# Examples

```
julia> using MultivariateAnomalies
julia> dc = hcat(rand(193) + 2* sin(0:pi/24:8*pi), rand(193) + 2* sin(0:pi/24:8*pi))
julia> cycles = get_MedianCycles(dc, 48)
```
