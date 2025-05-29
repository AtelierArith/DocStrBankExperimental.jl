```
get_MedianCycle(dat::Array{tp,1}, cycle_length::Int = 46)
```

returns the median annual cycle of a one dimensional data array, given the length of the annual cycle (presetting: `cycle_length = 46`). Can deal with some NaN values.

# Examples

```
julia> using MultivariateAnomalies
julia> dat = randn(90) + x = sind.(0:8:719)
julia> cycles = get_MedianCycle(dat, 48)
```
