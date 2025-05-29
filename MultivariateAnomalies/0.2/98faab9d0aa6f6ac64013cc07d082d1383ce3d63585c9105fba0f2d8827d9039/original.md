```
get_MedianCycle!(init_MC, dat::Array{tp,1})
```

Memory efficient version of `get_MedianCycle()`, returning the median cycle in `init_MC[3]`. The `init_MC` object should be created with `init_MedianCycle`. Can deal with some NaN values.

# Examples

```
julia> using MultivariateAnomalies
julia> dat = rand(193) + 2* sin(0:pi/24:8*pi)
julia> dat[100] = NaN
julia> init_MC = init_MedianCycle(dat, 48)
julia> get_MedianCycle!(init_MC, dat)
julia> init_MC[3]
```
