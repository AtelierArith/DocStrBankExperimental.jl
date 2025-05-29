```
sMSC(datacube, cycle_length)
```

subtract the median seasonal cycle from the datacube given the length of year `cycle_length`.

# Examples

```
julia> dc = hcat(rand(193) + 2* sin.(0:pi/24:8*pi), rand(193) + 2* sin.(0:pi/24:8*pi))
julia> sMSC_dc = sMSC(dc, 48)
```
